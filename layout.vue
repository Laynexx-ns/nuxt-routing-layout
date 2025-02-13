<script setup lang="ts">
import {Award, Zap, GalleryVertical, AtSign} from "lucide-vue-next";
import type {Component} from 'vue'

class Section {
  constructor(
      public Icon: Component,
      public Title: string,
      public Route: string
  ) {}
}

const sections : Section[] = [
  new Section(Award, 'Awards', '/awards'),
  new Section(Zap, 'Train', '/train'),
  new Section(GalleryVertical, 'Exercises', '/exercises'),
  new Section(AtSign, 'Profile', '/profile'),
]

const pageValue = ref('')

</script>

<template>
  <div class="xl:w-[1280px] w-screen flex flex-col h-full">
    <Tabs v-model="pageValue" class="w-full h-full items-center justify-center flex flex-col gap-2">

      <slot class="w-full h-full"/>

      <TabsList class="z-50 fixed bottom-4 border border-lx-border bg-black/60 h-[80px] flex w-fit flex-row backdrop-blur-xl gap-2 rounded-2xl p-1">
        <TabsTrigger
            v-for="(item, index) in sections"
            :key="index"
            :value="item.Title"
            @click="$router.push(item.Route)"
            class="relative flex flex-col items-center justify-center gap-1 w-[80px] h-full rounded-xl"
        >
          <div class="w-full flex flex-col items-center justify-center gap-2">
            <component :is="item.Icon" class="w-6 h-6 block" />
            <span class="text-center">{{ item.Title }}</span>
          </div>
        </TabsTrigger>
      </TabsList>
    </Tabs>
  </div>
</template>

<style scoped>

</style>
