<template>
    <div class="my-10" >
      <h1 class="text-3xl" >
        {{ title }}
      </h1>
      <hr class="border-amber-300">
      <p class="text-justify" ref="wrapperContent"> 
        {{ content }}
      </p>
    </div>
    
</template>

<script setup>

import { ref, watch, useTemplateRef, onMounted, watchEffect } from 'vue';

const props = defineProps(
    ['title', 'content', 'searchTerm']
)
const emite = defineEmits(['count'])

const title = ref(props.title)
const content = ref(props.content)
const termSearching = ref(props.searchTerm)
const matchedCount = ref(0)
const contentWrapperRef = useTemplateRef('wrapperContent')

const searchContent = () => {
    if (termSearching.value == ""){
        contentWrapperRef.value.innerHTML = content.value
        return
    }
    
    const reg = new RegExp(termSearching.value, "gi")
    const matched = content.value.match(reg)
    matchedCount.value = matched.length
    if (matched == null){
        contentWrapperRef.value.innerHTML = content.value
        matchedCount.value = 0
        return
    }
    const contentArray = content.value.split('')  
    matched.forEach(item => {
        const itemReg = new RegExp(item, "gi")
        contentWrapperRef.value.innerHTML = content.value.replace(itemReg, `<span class='bg-yellow-500'>${item}</span>`)
    });
}
watch(termSearching, ()=> {
    searchContent()
    emite('count', matchedCount.value)
})

</script>