<!--<script>

import emailjs from '@emailjs/browser';

export default {
  data(){
    return{
      anonim: false,
      fullName: '',
      posada: '',
      place: '',
      message: ''
    };
  },
  methods:{
    sendMail(){
      emailjs.send('service_8mri7jq', 'template_rtcfvqc',
      {
        email: 'malinka27032004@gmail.com',
        message: this.fullName + " " + this.message
      }, 'KWl6Tw9fWVpGHiqNR')
      .then((result) => {
            console.log('SUCCESS!', result.text);
        }, (error) => {
            console.log('FAILED...', error.text);
        });
    }
  }
}
</script>-->

<script>

import { ref } from 'vue'
import emailjs from '@emailjs/browser';

export default {
  setup() {
    var anonim = ref(false),
    fullName = ref(''),
    posada = ref(''),
    place = ref(''),
    message = ref('')
    
    function sendMail(){
      emailjs.send('service_8mri7jq', 'template_rtcfvqc',
      {
        email: 'malinka27032004@gmail.com',
        message: fullName.value + " " + message.value
      }, 'KWl6Tw9fWVpGHiqNR')
      .then((result) => {
        console.log('SUCCESS!', result.text);
      }, (error) => {
        console.log('FAILED...', error.text);
      });
    }
    return { anonim, fullName, posada, place, message, sendMail};
  },
}
</script>

<template>
  <h1 class="text-3xl text-gray-500 font-bold mt-0 mb-6">Повідомити про корупцію в навчальному закладі</h1>
  <form ref="form" @submit.prevent="sendEmail" class="w-full max-w-l">

    <div class="mb-6">
      <label class="block text-gray-500 font-bold md:text-left mb-1 md:mb-0 pr-4">
        ПІБ особи, яка ймовірно вчинила правопорушення
      </label>
      <input class="bg-gray-200 appearance-none border-2 border-gray-200 rounded" type="text" v-model="fullName">
    </div>

    <div class="mb-6">
      <label class="block text-gray-500 font-bold md:text-left mb-1 md:mb-0 pr-4">
        Посада
      </label>
      <input class="bg-gray-200 appearance-none border-2 border-gray-200 rounded" type="text" v-model="posada">
    </div>

    <div class="mb-6">
      <label class="block text-gray-500 font-bold md:text-left mb-1 md:mb-0 pr-4">
        Місце роботи
      </label>
      <input class="bg-gray-200 appearance-none border-2 border-gray-200 rounded" type="text" v-model="place">
    </div>

    <div class="mb-6">
      <label class="block text-gray-500 font-bold md:text-left mb-1 md:mb-0 pr-4">
        Опис ситуації
        </label>
      <textarea class="bg-gray-200 appearance-none border-2 border-gray-200 rounded" v-model="message"></textarea>
    </div>

    <div class="md:flex md:items-center mb-6">
      <label class="block text-gray-500 font-bold">
        <input type="checkbox" v-model="anonim">
        <span class="text-sm">
          Анонімне повідомлення
        </span>
      </label>
    </div>

    <div class="mb-6" v-if="!anonim">
      <label class="block text-gray-500 font-bold md:text-left mb-1 md:mb-0 pr-4">
        Ваше ПІБ
        </label>
      <input class="bg-gray-200 appearance-none border-2 border-gray-200 rounded" type="text">
    </div>

    <div class="mb-6" v-if="!anonim">
      <label class="block text-gray-500 font-bold md:text-left mb-1 md:mb-0 pr-4">
        Номер телефону
        </label>
      <input class="bg-gray-200 appearance-none border-2 border-gray-200 rounded" type="text" placeholder="123-45-678">
    </div>

    <div class="mb-6">
      <button class="shadow bg-purple-500 hover:bg-purple-400 focus:shadow-outline focus:outline-none text-white font-bold py-2 pl-2 pr-2" @click="sendMail()">
        Відправити
      </button>
    </div>

  </form>
</template>

<style>

</style>