<template>
  <div class="cards-template">
    <CardsTemplateFilters
      :users="users"
      @onUsersFilterChange="onUsersFilterChange"
      @onDateFilterChange="onDateFilterChange"
    />

    <div v-if="filteredPosts.length > 0" class="cards">
      <CardsTemplateItem
        v-for="(post, i) in filteredPosts"
        :key="i"
        :post="post"
      />
    </div>
    <span v-else
      >В дизайне этого не было, но здесь явно стоит писать, что по данным
      фильтрам ничего не найдено</span
    >
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data() {
    return {
      postsWithUser: null,
      users: null,
      filters: {
        users: [],
        dates: null,
      },
    }
  },
  async fetch() {
    const posts = await this.getPosts()
    this.users = await this.getUsers()
    this.postsWithUser = this.addUsersToPosts(posts, this.users)
  },
  computed: {
    filteredPosts() {
      return this.filterPostsByCreateDate(
        this.filterPostsByUserName(this.postsWithUser)
      )
    },
  },
  methods: {
    createRandomDate(start, end) {
      return new Date(
        start.getTime() + Math.random() * (end.getTime() - start.getTime())
      )
    },
    localizeDate(date) {
      const dateOptions = { day: 'numeric', month: 'long', year: 'numeric' }
      return date.toLocaleDateString('ru-RU', dateOptions).slice(0, -3)
    },
    filterPostsByUserName(posts) {
      return this.filters.users.length !== 0
        ? posts.filter((post) => this.filters.users.includes(post.userId))
        : posts
    },
    filterPostsByCreateDate(posts) {
      return this.filters.dates !== null
        ? posts.filter((post) => {
            const postTime = new Date(post.createdAt).getTime()
            const timeFrom = this.filters.dates[0]._d.getTime()
            const timeTo = this.filters.dates[1]._d.getTime()
            return postTime >= timeFrom && postTime <= timeTo
          })
        : posts
    },
    onUsersFilterChange(value) {
      this.filters.users = value
    },
    onDateFilterChange(value) {
      this.filters.dates = value
    },
    addUsersToPosts(posts, users) {
      return posts.map((post) => {
        const postWithUsers = post
        postWithUsers.createdAt = this.createRandomDate(
          new Date(2008, 7, 8),
          new Date()
        )
        postWithUsers.createdAtLocalized = this.localizeDate(
          postWithUsers.createdAt
        )
        postWithUsers.userName = users.find(
          (user) => user.id === postWithUsers.userId
        ).name
        return postWithUsers
      })
    },
    async getPosts() {
      try {
        const { data } = await axios.get(
          'https://jsonplaceholder.typicode.com/posts'
        )
        return data
      } catch (error) {
        throw new Error(error)
      }
    },
    async getUsers() {
      try {
        const { data } = await axios.get(
          'https://jsonplaceholder.typicode.com/users'
        )
        return data
      } catch (error) {
        throw new Error(error)
      }
    },
  },
}
</script>

<style lang="scss" scoped>
.cards {
  display: grid;
  grid-template-columns: repeat(3, 295px);
  grid-column-gap: 20px;
  grid-row-gap: 20px;

  width: 925px;
  @media (max-width: 990px) {
    grid-template-columns: repeat(2, 295px);
    width: 610px;
  }
  @media (max-width: 768px) {
    grid-template-columns: repeat(1, 100%);
    grid-row-gap: 10px;
    width: 100%;
  }
  &-template {
    display: flex;
    flex-direction: column;

    width: fit-content;
    margin: 0 auto;
    min-width: 300px;
    padding: 60px 0;
    @media (max-width: 768px) {
      width: 100%;
      padding: 32px 15px;
    }
  }
}
</style>
