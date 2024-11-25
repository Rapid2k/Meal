<template>
    <div >
        <header>
            <Navbar/>
        </header>

        <main>
        <slot></slot>
        </main>
        <footer></footer>

    </div>
</template>

<script setup>
    
        
   
    import { onMounted } from 'vue'
import { useFlowbite } from '~/composables/useFlowbite';

// initialize components based on data attribute selectors
onMounted(() => {
    useFlowbite(() => {
        initFlowbite();
    })
})
</script>

<style >

</style>