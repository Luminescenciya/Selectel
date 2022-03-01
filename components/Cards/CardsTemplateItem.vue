<template>
  <a-card class="card" :title="post.title">
    <div class="card__body">
      {{ post.body }}
    </div>
    <div class="card__bottom">
      <span class="card__tag card__author"> {{ post.userName }} </span>
      <span class="card__tag card__date"> {{ post.createdAtLocalized }} </span>
    </div>
  </a-card>
</template>

<script>
export default {
  props: {
    post: { type: Object, default: null },
  },
}
</script>

<style lang="scss" scoped>
.card {
  &__tag {
    font-size: 12px;
    line-height: 20px;
    padding: 0 8px;
    border-radius: 10px;
    box-sizing: border-box;
    &:not(:last-child) {
      margin-right: 10px;
    }
  }
  &__author {
    color: #ffffff;
    background: #092433;
  }
  &__date {
    color: #595959;
    border: 1px solid #e8e8e8;
    white-space: nowrap;
  }
  &__bottom {
    margin-top: auto;
    padding-top: 16px;
    & > * {
      margin-top: 16px;
    }
  }
}
</style>
