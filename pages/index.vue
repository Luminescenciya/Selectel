<template>
  <main class="main">
    <Carousel :pages="pages" />
    <CardsTemplate />
  </main>
</template>

<script>
export default {
  data() {
    return {
      pages: [
        {
          image: '/CarouselBg.png',
          title: 'IT-инфраструктура для бизнеса',
          description:
            'Мы предлагаем комплексные решения для всех уровней бизнеса: от индивидуальных предпринимателей до крупных международных компаний. Более 20 000 клиентов по всему миру доверяют Selectel.',
        },
        {
          image: '/CarouselBg.png',
          title: 'IT-инфраструктура для бизнеса',
          description:
            'Мы предлагаем комплексные решения для всех уровней бизнеса: от индивидуальных предпринимателей до крупных международных компаний. Более 20 000 клиентов по всему миру доверяют Selectel.',
        },
        {
          image: '/CarouselBg.png',
          title: 'IT-инфраструктура для бизнеса',
          description:
            'Мы предлагаем комплексные решения для всех уровней бизнеса: от индивидуальных предпринимателей до крупных международных компаний. Более 20 000 клиентов по всему миру доверяют Selectel.',
        },
      ],
    }
  },
}
</script>

<style lang="scss" scoped>
.main {
  padding-top: 88px;
  flex-grow: 1;
  @media (max-width: 768px) {
    padding-top: 56px;
  }
}
</style>
