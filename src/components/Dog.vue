<template>
        <div class="bg-white border-2 border-indigo-200 rounded-lg flex-grow">
        <div class="p-4 grid grid-cols-1 justify-items-start items-start">
         <h3>{{ name }}</h3>  
             <p>{{ weight }}  {{ length }}</p>
             <p>{{ hobbies }}</p>
             <p>{{ motto }}</p>
        </div>
        </div>
</template>

<script>
export default {
props: ['id','name','handicap','weight','length','hobbies','motto','image']

}
</script>

<style>

</style>