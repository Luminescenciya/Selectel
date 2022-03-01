<template>
  <footer class="footer">
    <div class="footer__container">
      <div class="footer__logo">
        <a href="https://selectel.ru/"
          ><img class="footer__logo-image" src="../assets/footer-logo.svg"
        /></a>
      </div>
      <div class="footer__copyright">
        <p class="footer__copyright-text">© ООО «Селектел», 2008—2022</p>
        <p class="footer__licenses">
          Лицензия на телематические услуги №176267
        </p>
      </div>
      <div class="footer__menu" :span="14">
        <a>Серверы</a>
        <a>Оборудование</a>
        <a>Дата-центры</a>
        <a>Блог</a>
        <a>Облако</a>
        <a>Решения</a>
        <a>О компании</a>
        <a>Офисы</a>
      </div>
      <div class="footer__social" :span="14">
        <a class="footer__social-icon"
          ><img src="../assets/social_icons/Tg.svg"
        /></a>
        <a class="footer__social-icon"
          ><img src="../assets/social_icons/Facebook.svg"
        /></a>
        <a class="footer__social-icon"
          ><img src="../assets/social_icons/Vk.svg"
        /></a>
        <a class="footer__social-icon"
          ><img src="../assets/social_icons/Twitter.svg"
        /></a>
        <a class="footer__social-icon"
          ><img src="../assets/social_icons/HH.svg"
        /></a>
      </div>
    </div>
  </footer>
</template>

<style lang="scss" scoped>
.footer {
  background: #092433;
  &__container {
    padding: 80px 23px;
    display: grid;
    grid-template-areas:
      'logo menu'
      'copyright social';
    grid-template-columns: 5fr 7fr;
    @media (max-width: 990px) {
      padding: 34px 16px;
      grid-template-areas:
        'logo'
        'social'
        'menu'
        'copyright';
      grid-template-columns: 1fr;
    }
  }
  &__logo {
    grid-area: logo;
    &-image {
      @media (max-width: 990px) {
        height: 50px;
      }
      @media (max-width: 768px) {
        height: 30px;
      }
    }
  }
  &__copyright {
    grid-area: copyright;

    font-size: 14px;
    line-height: 20px;
    color: rgba(255, 255, 255, 0.8);
    opacity: 0.5;

    width: 220px;
    margin-top: 32px;

    @media (max-width: 768px) {
      width: auto;
      margin-top: 48px;
      font-size: 12px;
    }
    & p {
      margin-bottom: 0;
    }
  }
  &__licenses {
    margin-top: 6px;
  }
  &__menu {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-row-gap: 17px;
    align-content: center;
    grid-area: menu;
    @media (max-width: 990px) {
      grid-template-columns: repeat(4, 1fr);
      grid-row-gap: 12px;

      margin-top: 32px;
    }
    @media (max-width: 768px) {
      grid-template-columns: 5fr 7fr;
    }

    & a {
      font-weight: 500;
      font-size: 16px;
      line-height: 24px;
      color: #ffffff;

      @media (max-width: 768px) {
        font-size: 14px;
      }
    }
  }
  &__social {
    margin-top: 79px;
    display: grid;
    grid-template-columns: repeat(auto-fit, 24px);
    grid-gap: 16px;
    grid-area: social;

    @media (max-width: 990px) {
      margin-top: 24px;
    }
  }
}
</style>
