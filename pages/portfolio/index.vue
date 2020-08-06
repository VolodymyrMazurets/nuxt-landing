<template>
  <div class="portfolio">
    <h1 class="portfolio__title">Portfolio</h1>
    <a-radio-group v-model="value">
      <a-radio-button value="All works">
        All works
      </a-radio-button>
      <a-radio-button value="Graphics Design">
        Graphics Design
      </a-radio-button>
      <a-radio-button value="Web Design">
        Web Design
      </a-radio-button>
      <a-radio-button value="Web Devlopment">
        Web Devlopment
      </a-radio-button>
    </a-radio-group>
    <transition-group name="list" tag="ul" class="portfolio__gallery">
      <li class="portfolio__gallery-item" v-for="item in filteredList" :key="item.img">
        <img :src="item.img" alt="" />
      </li>
    </transition-group>
  </div>
</template>
<script>
export default {
  name: 'Portfolio',
  head() {
    return {
      title: 'Portfolio'
    }
  },
  data() {
    return {
      list: [
        {
          img: '1.jpg',
          category: 'Graphics Design'
        },
        {
          img: '2.jpg',
          category: 'Web Design'
        },
        {
          img: '3.jpg',
          category: 'Web Devlopment'
        },
        {
          img: '4.jpg',
          category: 'Graphics Design'
        },
        {
          img: '5.jpg',
          category: 'Web Devlopment'
        },
        {
          img: '6.jpg',
          category: 'Graphics Design'
        },
        {
          img: '7.jpg',
          category: 'Web Design'
        },
        {
          img: '8.jpg',
          category: 'Web Design'
        }
      ],
      value: 'All works'
    }
  },
  computed: {
    filteredList() {
      const { value, list } = this
      if (value === 'All works') {
        return list
      } else {
        return list.filter(({ category }) => category === value)
      }
    }
  }
}
</script>
<style lang="scss">
.portfolio {
  text-align: center;
  &__title {
    text-transform: uppercase;
    font-weight: 700;
    text-align: center;
  }
  &__list {
    list-style: none;
    display: flex;
    justify-content: center;
    margin-bottom: 32px;
  }
  &__item {
    margin-right: 16px;
    &:last-child {
      margin-right: 0;
    }
  }
  &__gallery {
    display: flex;
    flex-wrap: wrap;
    margin: 0 -15px;
    list-style: none;
  }
  &__gallery-item {
    padding: 15px;
    flex-basis: 25%;
    max-width: 25%;
  }
  .list {
    &-move {
      transition: all 600ms ease-in-out 50ms;
    }
    &-enter-active {
      transition: all 500ms ease-out;
    }

    &-leave-active {
      transition: all 500ms ease-in;
      position: absolute;
      z-index: 0;
    }

    &-enter,
    &-leave-to {
      opacity: 0;
    }
    &-enter {
      transform: scale(0.9);
    }
  }
}
</style>
