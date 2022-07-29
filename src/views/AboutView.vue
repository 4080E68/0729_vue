<template>
  <div class="container">
    <h1>This is an about page</h1>
    <Card></Card>
    <Form @submit="onSubmit" v-slot="{ errors, values }">
      <div class="mb-3">
        <label for="email" class="form-label">Email</label>
        <Field
          id="email"
          name="email"
          type="email"
          class="form-control"
          placeholder="請輸入 Email"
          rules="email|required"
          :class="{
            'is-invalid': errors['email'],
            'is-valid': !errors['email'] && values['email']
          }"
        ></Field>
        <error-message name="email" class="invalid-feedback"></error-message>
      </div>

      <div class="mb-3">
        <label for="name" class="form-label">姓名</label>
        <Field
          id="name"
          name="name"
          type="text"
          class="form-control"
          :rules="nameCheck"
          :class="{
            'is-invalid': errors['name'],
            'is-valid': !errors['name'] && values['name']
          }"
          placeholder="請輸入姓名"
        ></Field>
        <error-message name="name" class="invalid-feedback"></error-message>
      </div>

      <div class="mb-3">
        <label for="phone" class="form-label">電話</label>
        <Field
          id="phone"
          name="電話"
          type="text"
          class="form-control"
          placeholder="請輸入電話"
          :rules="isPhone"
          :class="{
            'is-invalid': errors['電話'],
            'is-valid': !errors['電話'] && values['電話']
          }"
        ></Field>
        <error-message name="電話" class="invalid-feedback"></error-message>
      </div>

      <div class="mb-3">
        <label for="region" class="form-label">地區</label>
        <Field
          as="select"
          id="region"
          name="地區"
          class="form-control"
          rules="required"
          :class="{ 'is-invalid': errors['地區'], 'is-valid': values['地區'] }"
        >
          <option value="" disabled selected>請選擇地區</option>
          <option value="台北市">台北市</option>
          <option value="高雄市">高雄市</option>
        </Field>
        <error-message name="地區" class="invalid-feedback"></error-message>
      </div>

      <div class="mb-3">
        <label for="address" class="form-label">地址</label>
        <input
          id="address"
          name="地址"
          type="text"
          class="form-control"
          placeholder="請輸入地址"
        />
        <span class="invalid-feedback"></span>
      </div>

      <button class="btn btn-primary" type="submit">Submit</button>
    </Form>
  </div>
</template>

<script>
import Card from '@/components/Card'

export default {
  data() {
    return {
      email: '',
      name: ''
    }
  },
  methods: {
    onSubmit(value, { resetForm }) {
      console.log(this.user)
      console.log(value)
      console.log('送出成功')
      resetForm()
    },

    isPhone(value) {
      const phoneNumber = /^(09)[0-9]{8}$/
      console.log(value)
      return phoneNumber.test(value) ? true : '需要正確的電話號碼'
    },
    nameCheck(value) {
      const name = 'aaa'
      console.log(value)
      if (value !== undefined) {
        return value !== name ? true : '此名稱已存在'
      } else {
        return '此欄位必須填寫'
      }
    }
  },
  components: {
    Card
  }
}
</script>
