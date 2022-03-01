<template>
  <div class="cards">
    <a-card v-for="(item, i) in Array(3)" :key="i" class="card">
      <a-skeleton slot="title" :active="true" :paragraph="false" />
      <a-skeleton :active="true" />
    </a-card>
  </div>
</template>
