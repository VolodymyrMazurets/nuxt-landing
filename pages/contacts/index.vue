<template>
  <div class="contacts">
    <div class="container">
      <h1 class="contacts__title">GET IN TOUCH</h1>
      <a-form :form="form" :label-col="{ span: 5 }" :wrapper-col="{ span: 12 }" @submit="handleSubmit">
        <div class="contacts__row">
          <a-form-item
            :style="{ width: '100%', paddingLeft: '15px', paddingRight: '15px' }"
            :wrapper-col="{ span: 24 }"
          >
            <a-input
              placeholder="Your Name"
              v-decorator="['name', { rules: [{ required: true, message: 'Please input your name!' }] }]"
            />
          </a-form-item>
          <a-form-item
            :style="{ width: '100%', paddingLeft: '15px', paddingRight: '15px' }"
            :wrapper-col="{ span: 24 }"
          >
            <a-input
              placeholder="Your Email"
              v-decorator="[
                'email',
                { rules: [{ required: true, type: 'email', message: 'Please input your email!' }] }
              ]"
            />
          </a-form-item>
        </div>
        <div class="contacts__row">
          <a-form-item
            :style="{ width: '100%', paddingLeft: '15px', paddingRight: '15px' }"
            :wrapper-col="{ span: 24 }"
          >
            <a-input
              placeholder="Your Website"
              v-decorator="['website', { rules: [{ required: true, message: 'Please input your website!' }] }]"
            />
          </a-form-item>
          <a-form-item
            :style="{ width: '100%', paddingLeft: '15px', paddingRight: '15px' }"
            :wrapper-col="{ span: 24 }"
          >
            <a-input
              placeholder="Your Subject"
              v-decorator="['subject', { rules: [{ required: true, message: 'Please input your subject!' }] }]"
            />
          </a-form-item>
        </div>
        <a-form-item :style="{ width: '100%', paddingLeft: '15px', paddingRight: '15px' }" :wrapper-col="{ span: 24 }">
          <a-textarea
            placeholder="Your message"
            :auto-size="{ minRows: 5, maxRows: 16 }"
            v-decorator="['message', { rules: [{ required: true, message: 'Please input your message!' }] }]"
          />
        </a-form-item>
        <a-form-item :wrapper-col="{ span: 12, offset: 11 }">
          <a-button type="primary" html-type="submit">
            Submit
          </a-button>
        </a-form-item>
      </a-form>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Contacts',
  head() {
    return {
      title: 'Contact Us'
    };
  },
  data() {
    return {
      formLayout: 'horizontal',
      form: this.$form.createForm(this, { name: 'coordinated' }),
      formData: {
        name: '',
        email: '',
        website: '',
        subject: '',
        message: ''
      }
    };
  },
  methods: {
    handleSubmit(e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log('Received values of form: ', values);
        }
      });
    }
  }
};
</script>
<style lang="scss">
.contacts {
  background: #373737 url(~static/map-bg.png) no-repeat center;
  &::before {
    content: '';
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    left: 0;
    background: rgba(55, 55, 55, 0.8);
    display: block;
    z-index: 0;
  }
  .container {
    max-width: 800px;
    height: 100%;
    width: 100%;
    margin: 0 auto;
    padding: 24px 24px 0;
    display: flex;
    flex-direction: column;
    align-items: stretch;
    justify-content: center;
  }
  &__title {
    color: #fff;
    text-transform: uppercase;
    font-weight: 700;
    text-align: center;
    z-index: 1;
  }
  &__row {
    display: flex;
    justify-content: stretch;
  }
  & .ant-input {
    background-color: transparent;
    height: 40px;
    border: 1px solid #fff;
    color: #fff;
    border-radius: 0;
    &:focus {
      border-color: #52e5ab;
    }
  }
  & .has-error .ant-input,
  .has-error .ant-input:hover {
    background-color: transparent;
  }
}
</style>
