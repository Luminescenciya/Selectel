<template>
  <header class="header">
    <div class="header__left">
      <a href="https://selectel.ru/"
        ><img class="header__logo" src="../assets/header-logo.svg"
      /></a>
    </div>
    <div class="header__right">
      <a class="header__phone" href="tel:88005550675"
        ><span class="header__pc">8 800 555 06 75</span>
        <img class="header__mobile" src="../assets/phone.svg"
      /></a>
      <a class="header__email" href="mailto:sales@selectel.ru"
        ><span class="header__pc">sales@selectel.ru</span>
        <img class="header__mobile" src="../assets/mail.svg"
      /></a>
    </div>
  </header>
</template>

<style lang="scss" scoped>
.header {
  display: grid;
  grid-template-columns: 1fr 5fr 5fr 1fr;
  grid-template-areas: '. left right .';
  align-items: center;

  position: fixed;
  z-index: 100;

  width: 100%;
  height: 88px;
  background: #ffffff;
  @media (max-width: 990px) {
    padding: 0 15px;
  }
  @media (max-width: 768px) {
    height: 56px;
    padding: 0 15px;
    grid-template-columns: 1fr 1fr;
    grid-template-areas: 'left right';
  }
  &__pc {
    @media (max-width: 768px) {
      display: none;
      width: 0;
    }
  }
  &__mobile {
    display: none;
    @media (max-width: 768px) {
      display: block;
    }
  }
  &__left {
    grid-area: left;
  }
  &__right {
    grid-area: right;
    display: flex;
    justify-content: flex-end;
    & > *:not(:last-child) {
      margin-right: 48px;
      @media (max-width: 768px) {
        margin-right: 17px;
      }
    }
  }

  &__phone,
  &__email {
    font-weight: 500;
    font-size: 16px;
    line-height: 22px;
    &:hover {
      color: inherit;
    }
  }
}
</style>
