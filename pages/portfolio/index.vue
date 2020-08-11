<template>
  <div class="portfolio">
    <a-modal
      :visible="visible"
      @cancel="visible = false"
      :footer="null"
      width="fit-content"
      wrapClassName="portfolio__modal"
    >
      <img :src="imageSrc" alt="" />
    </a-modal>
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
      <li class="portfolio__gallery-item" v-for="item in filteredList" :key="item.img" @click="openModal(item.img)">
        <img :src="item.img" alt="" />
      </li>
    </transition-group>
  </div>
</template>
<script>
import '../../assets/portfolio.scss';

export default {
  name: 'Portfolio',
  head() {
    return {
      title: 'Portfolio'
    };
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
      value: 'All works',
      visible: false,
      imageSrc: null
    };
  },
  computed: {
    filteredList() {
      const { value, list } = this;
      if (value === 'All works') {
        return list;
      } else {
        return list.filter(({ category }) => category === value);
      }
    }
  },
  methods: {
    openModal(img) {
      this.imageSrc = img;
      this.visible = true;
    }
  },
  mounted() {}
};
</script>
