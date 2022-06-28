<template>
  <div class="wrapper">

    <header>
      <div class="logo_img">
        <a href="/">
          <img src="../src/images/logo.png" width="60" height="60px" />
        </a>
      </div>
      <div class="logo_title">
          <h1>VUETTER</h1>
      </div>
    </header>
    
    <div class="wrapper-content">
      <div class="view">
        <div class="container">
          <Twit_Form @onSubmit="handleSubmit" />
          <Twit_list :items="items" />
        </div>
      </div>
    </div>
    

  </div>
</template>

<script>
import { ref } from 'vue'

import Twit_list from '@/components/Twit_list'
import Twit_Form from '@/components/Twit_Form'

export default {
  components: { Twit_Form, Twit_list },
  setup() {
    const items = ref([
      {
        id: 1,
        body: 'hello vue 3',
        likes: 12,
        avatar: `https://avatars.dicebear.com/api/identicon/1.svg`,
        date: new Date(Date.now()).toLocaleString()
      },
      {
        id: 2,
        body: 'hello world',
        likes: 6,
        avatar: `https://avatars.dicebear.com/api/identicon/2.svg`,
        date: new Date(Date.now()).toLocaleString()
      }
    ])
    const handleSubmit = item => items.value.push(item)
    return {
      items,
      handleSubmit
    }
  }
}

</script>




