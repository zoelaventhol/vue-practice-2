<template>
    <div class="Featured">
        <img v-if="featured" :src="featured"/>
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
/* add style to feat img */
.Featured img {
    height: 200px;
    border: 8px solid gray
}
</style>