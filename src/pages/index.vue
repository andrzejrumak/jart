<script setup lang="ts">
import { useRouter } from 'vue-router'
import { useI18n } from 'vue-i18n'
import { useFetch } from '@vueuse/core'
import { ref, reactive } from 'vue'

const { data, execute } = useFetch('https://v2.jokeapi.dev/joke/Any?blacklistFlags=religious&type=twopart').get().json()

const name = ref('')
// console.log(data.value)
const router = useRouter()
const go = () => {
  if (name.value)
    router.push(`/hi/${encodeURIComponent(name.value)}`)
}

const { t } = useI18n()
</script>

<template>
  <div class="text-yellow-600">
    <img class="object-none h-48 w-full my-6" src="/artj.png">
    <p class=" text-4xl">
      Joanna Rumak - oferta
    </p>
    <p>
      <em class="text-sm opacity-75">{{ t('opis.oferta') }}</em>
    </p>
    <div>
      <div class="inline-flex my-5">
        <icon-park-outline:bring-forward class="text-4xl m-auto" />
        <h3 class="text-center text-4xl mx-4">
          Przegląd szafy
        </h3>
      </div>
    </div>
    <div>
      <div class="inline-flex my-5">
        <icon-park-outline:color-filter class="text-4xl m-auto" />
        <h3 class="text-center text-4xl mx-4">
          Analiza kolororystyczna
        </h3>
      </div>
    </div>
    <div>
      <div class="inline-flex my-5">
        <icon-park-outline:abdominal class="text-4xl m-auto" />
        <h3 class="text-center text-4xl mx-4">
          Typ sylwetki
        </h3>
      </div>
    </div>
    <div>
      <div class="inline-flex my-5">
        <icon-park-outline:arrow-keys class="text-4xl m-auto" />
        <h3 class="text-center text-4xl mx-4">
          Szafa kapsułowa
        </h3>
      </div>
    </div>
    <div>
      <div class="inline-flex my-5">
        <icon-park-outline:shopping-cart-one class="text-4xl m-auto" />
        <h3 class="text-center text-4xl mx-4">
          Zakupy ze stylistką
        </h3>
      </div>
    </div>
    <div>
      <div class="inline-flex my-5">
        <icon-park-outline:paper-money-two class="text-4xl m-auto" />
        <h3 class="text-center text-4xl mx-4">
          Wydatki na ubrania
        </h3>
      </div>
    </div>
  </div>
  <div class="text-red-500 m-5 text-center text-xl">
    <div>
      <div>
        Taki żarcik na koniec
      </div>
      <button class="text-red-500 m-5 bg-red-100 border-red-500 p-1 rounded-xl text-center text-xl" @click="execute">
        Następny
      </button>
    </div>
    <div v-if="data">
      <div>
        {{ data.setup }}
      </div>
      <div>
        {{ data.delivery }}
      </div>
    <!-- <div v-if="tp">
      {{ zart }}
    </div>
    <div v-else>
      <div v-if="zart.setup">
        <p class="text-red-500 m-5 text-center">
          {{ zart.setup }}
        </p>
      </div>

      <p class="text-red-500 m-5 text-center">
        {{ zart.delivery }}
      </p>
    </div> -->
    </div>
  </div>
</template>

<route lang="yaml">
meta:
  layout: home
</route>
