<template>
    <div>
        <section class="py-5 ">
             
            <div class="container m-auto ">
                <!-- search Box -->
                <div>
                    <form class="max-w-sm mx-auto">
    <label for="countries" class=" block mb-2 text-sm font-medium text-gray-900 dark:text-white">Select an option</label>
    <select 
    v-model="query " 
  
    @change="getProduct (query)"  
    
  
    class=   "bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full 
     p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500">
      <option selected>Chicken</option>
      <option :value="category.strCategory" v-for="(category,index) in cate.categories" :key="index">{{ category.strCategory }}</option>
  
    </select>
  </form>

                </div>
                <!-- product -->
                <div v-if="pending" class="flex justify-center h-screen items-center">
                    <img  src="~/assets/images/load.gif" alt="">
                    
                </div>
                    <div class="grid grid-cols-4 gap-5 my-2 v-else">
    <div v-for="( product ,index) in sea.meals " :key="index" >
        <Card :product="product " />
    </div>

</div>

                

            </div>
        </section>
    </div>
</template>

<script setup>

const query ="";
const url = ref("https://www.themealdb.com/api/json/v1/1/filter.php?c=Chicken");
const { data: cate  }=useFetch(
"https://www.themealdb.com/api/json/v1/1/categories.php"
);
const {data:sea,pending     }=useFetch(
    url,{refetch: true});

    function getProduct(category){
        url.value=`https://www.themealdb.com/api/json/v1/1/filter.php?c=${category}`
    }

</script>

<style scoped>

</style>







<!-- product -->
