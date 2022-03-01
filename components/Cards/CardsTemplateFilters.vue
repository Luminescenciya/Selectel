<template>
  <div class="filters">
    <a-select
      mode="multiple"
      class="select"
      placeholder="Выберите автора"
      :max-tag-count="0"
      :max-tag-placeholder="`Выбрано авторов: ${usersSelectCounter}`"
      @change="onUsersFilterChange"
    >
      <a-icon slot="suffixIcon" type="smile" />
      <a-select-option v-for="user in users" :key="user.id" :value="user.id">
        {{ user.name }}
      </a-select-option>
    </a-select>
    <a-range-picker :placeholder="['От', 'До']" @change="onDateFilterChange" />
  </div>
</template>

<script>
export default {
  props: {
    users: { type: Array, default: null },
  },
  data() {
    return {
      usersSelectCounter: 0,
    }
  },
  methods: {
    onUsersFilterChange(value) {
      this.usersSelectCounter = value.length
      return this.$emit('onUsersFilterChange', value)
    },
    onDateFilterChange(value) {
      this.$emit('onDateFilterChange', value)
    },
  },
}
</script>

<style lang="scss" scoped>
.select {
  width: 295px;
  @media (max-width: 768px) {
    width: auto;
  }
}
.filters {
  display: flex;
  width: 100%;
  padding: 16px 0;
  margin-bottom: 24px;

  position: sticky;
  top: 88px;
  z-index: 101;

  background: #ffffff;
  @media (max-width: 768px) {
    flex-direction: column;
    top: 56px;
    margin-bottom: 16px;
  }
  & > *:not(:last-child) {
    margin-right: 20px;
    @media (max-width: 768px) {
      margin-right: 0;
      margin-bottom: 12px;
    }
  }
}
</style>
