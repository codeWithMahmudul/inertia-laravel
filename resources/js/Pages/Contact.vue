<template>
  <div>
    <AppLayout>
      <header class="bg-white shadow">
        <div class="mx-auto max-w-7xl px-4 py-6 sm:px-6 lg:px-8">
          <h1 class="text-3xl font-bold tracking-tight text-gray-900">Contact</h1>
        </div>
      </header>
      <main>
        <div class="mx-auto max-w-7xl py-6 sm:px-6 lg:px-8">
          <div class="border-b border-gray-900/10 pb-12">
            <form @submit.prevent="submit">
              <h2 class="text-base font-semibold leading-7 text-gray-900">Personal Information</h2>
              <p class="mt-1 text-sm leading-6 text-gray-600">Use a permanent address where you can receive mail.</p>

              <div class="mt-10 grid grid-cols-1 gap-x-6 gap-y-8 sm:grid-cols-6">
                <div class="sm:col-span-3">
                  <label for="name" class="block text-sm font-medium leading-6 text-gray-900">Name</label>
                  <div class="mt-2">
                    <input type="text" name="name" id="name" autocomplete="given-name"
                      class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                      v-model="form.name" />
                    <p class="text-red-800" v-if="form.errors.name">{{ form.errors.name }}</p>
                  </div>
                </div>



                <div class="sm:col-span-4">
                  <label for="email" class="block text-sm font-medium leading-6 text-gray-900">Email address</label>
                  <div class="mt-2">
                    <input id="email" name="email" type="email" autocomplete="email"
                      class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                      v-model="form.email" />
                    <p class="text-red-800" v-if="form.errors.email">{{ form.errors.email }}</p>
                  </div>
                </div>



                <div class="col-span-full">
                  <label for="subject" class="block text-sm font-medium leading-6 text-gray-900">Subject</label>
                  <div class="mt-2">
                    <input type="text" name="subject" id="subjects" autocomplete="subject"
                      class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                      v-model="form.subject" />
                    <p class="text-red-800" v-if="form.errors.subject">{{ form.errors.subject }}</p>
                  </div>
                </div>

                <div class="col-span-full">
                  <label for="message" class="block text-sm font-medium leading-6 text-gray-900">Message</label>
                  <div class="mt-2">
                    <textarea type="text" name="message" id="message" autocomplete="message"
                      class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                      v-model="form.message"> </textarea>
                    <p class="text-red-800" v-if="form.errors.message">{{ form.errors.message }}</p>
                  </div>
                </div>

              </div>
              <div class="mt-6 flex items-center justify-end gap-x-6">
                <button type="submit"
                  class="rounded-md bg-indigo-600 px-3 py-2 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">Save</button>
              </div>
            </form>
          </div>
        </div>
      </main>
    </AppLayout>
  </div>
</template>
    
<script setup>
import AppLayout from "../Layouts/App.vue";
import { reactive } from 'vue'
import { useForm } from '@inertiajs/vue3'

const form = useForm({
  name: null,
  email: null,
  subject: null,
  message: null,
})
function submit() {
  form.post('/contact')
}
</script>