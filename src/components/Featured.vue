<template>
    <div class="Featured">
        [featured image]
        <img :src="featured"/>
    </div>
</template>
    
<script>
    export default {
        name: 'Featured',
        components: {},
        data() {
            return {}
        },
        methods: {},
        // receive props from parent
        props: ['featured']
    }
</script>
    
<style>
</style>