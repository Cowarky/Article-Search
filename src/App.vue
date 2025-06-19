
<template>
  <div class="bg-amber-50 h-screen p-20"> 
    <SearchBar @search="(term) => SetInput(term)" :count = "finalCount"/>
    <Article 
    @count = "(count) => SetCount(count)"
    :searchTerm="GetInput()" 
    :title="'Indias TCS says none of its systems were compromised in M&S hack'" 
    :content="'Tata Consultancy Services said none of its systems or users were compromised as part of the cyberattack that led to the theft of customer data at retailer Marks and Spencer , its client of more than a decade.'"
    
    />

    <Article 
    @count = "(count) => SetCount(count)"
    :searchTerm="GetInput()" 
    :title="'Amazon to invest $233 million in India to expand operations infrastructure, improve tech'" 
    :content="'In June 2023, the e-commerce major which competes with Walmarts Flipkart and billionaire Mukesh Ambanis Reliance Retail in India - had said it will take its investments in the country to $26 billion by 2030, without providing a breakdown. The new investment will be used to launch new sites and upgrade existing facilities across its fulfilment and delivery network, improving speed and processing capacity, it said. Additionally, Amazon plans to use technology to alert delivery associates about unsafe speeds and ensure equitable distribution of delivery routes. Some of the funds will also be used to expand initiatives to improve the health and financial well-being of its employees, the company said. In March, Indias information technology ministry said Amazons cloud services provider, Amazon Web Services, will invest about $8.2 billion in the country.'"/>
  </div>
</template>

<script setup>
import SearchBar from './components/SearchBar.vue';
import Article from './components/Article.vue';
import { onMounted } from 'vue';
import { ref } from 'vue';
import { watch } from 'vue';
import { onBeforeMount } from 'vue';
import { computed } from 'vue';
import { onUpdated } from 'vue';

const termInput = ref()
const termCount = ref([])

function SetInput(term){
  termInput.value = term
}
function SetCount(count){
  termCount.value.push(count) 
}
function GetInput () {
  return termInput
}
const finalCount = computed(() => {
  let result = 0

  termCount.value.forEach(element => {
    result+=element
  });  
  
  return result
})
watch(termCount, ()=> {
  
})

</script>