<script setup>
import { reactive } from 'vue';
import { Inertia } from '@inertiajs/inertia';
import ValidationErrors from '@/Components/ValidationErrors.vue';

defineProps({
  errors: Object
})

const from =reactive({
  title: null,
  content: null
})

const submitFunction = () => {
  Inertia.post('/inertia', from)
}
</script>

<template>
  <ValidationErrors :errors="errors" />
  <form @submit.prevent="submitFunction">
    <input  type="text" name="title" v-model="from.title"> <br>
    <div v-if="errors.title">{{ errors.title }}</div>
    <input  type="text" name="content" v-model="from.content">
    <div v-if="errors.content">{{ errors.content }}</div>
    <button>送信</button>
  </form>
</template>