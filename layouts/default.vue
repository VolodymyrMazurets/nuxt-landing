<template>
  <a-layout class="default">
    <a-layout-content class="default__content"><Nuxt /></a-layout-content>
    <a-layout-footer class="default__footer">
      <ul class="default__nav">
        <nuxt-link tag="li" to="/" active-class="_active" exact class="default__item">
          <span class="default__router-link">
            <img src="~static/profile-pic.jpg" class="img-responsive" width="190" height="190" alt="" />
          </span>
        </nuxt-link>
        <nuxt-link tag="li" to="/about" active-class="_active" class="default__item">
          <span class="default__router-link">
            <a-icon class="default__icon" type="user" />
            <span>about me</span>
          </span>
        </nuxt-link>
        <nuxt-link tag="li" to="/resume" active-class="_active" class="default__item">
          <span class="default__router-link">
            <a-icon class="default__icon" type="gift" />
            <span>resume</span>
          </span>
        </nuxt-link>
        <nuxt-link tag="li" to="/portfolio" active-class="_active" class="default__item">
          <span class="default__router-link">
            <a-icon class="default__icon" type="camera" />
            <span>portfolio</span>
          </span>
        </nuxt-link>
        <nuxt-link tag="li" to="/blog" active-class="_active" class="default__item">
          <span class="default__router-link">
            <a-icon class="default__icon" type="message" />
            <span>blog</span>
          </span>
        </nuxt-link>
        <nuxt-link tag="li" to="/contacts" active-class="_active" class="default__item">
          <span class="default__router-link">
            <a-icon class="default__icon" type="phone" />
            <span>Contact us</span>
          </span>
        </nuxt-link>
      </ul>
    </a-layout-footer>
  </a-layout>
</template>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
$style: 'default';
.#{$style} {
  height: 100vh;
  &__nav {
    list-style: none;
    display: flex;
    align-items: stretch;
    margin: 0;
  }
  &__item {
    flex-basis: calc(100% / 6);
    flex: 1 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    border: 1px solid #c3c3c3;
    position: relative;
    cursor: pointer;
    &:before {
      content: '';
      display: block;
      position: absolute;
      top: -3px;
      left: 0;
      right: 0;
      height: 3px;
      transition: all .3s ease;
    }
    &._active {
      &:before {
        background-color: #52e5ab;
      }
      .#{$style}__icon {
        color: #52e5ab;
      }
    }
  }
  &__router-link {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    color: black;
    font-size: 14px;
    text-transform: uppercase;
  }
  &__icon {
    font-size: 30px;
    margin-bottom: 6px;
    transition: color .3s ease;
  }
  &__footer {
    padding: 0 50px;
  }
  &__content {
    display: flex;
    max-width: 1200px;
    width: 100%;
    margin: auto;
    padding: 24px 24px 0;
    & > * {
      flex: 1 1;
    }
  }
}
</style>
