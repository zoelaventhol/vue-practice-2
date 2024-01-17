<template>
    <div class="Content">
        <!-- render featured image grid & pass featured data -->
        <Featured />

        <!-- Render image grid & pass images to component. Add event listener to update "featured" @setFeatured -->
        <ImageGrid 
            :images="images"
            @setFeatured="(url) => this.featured = url"
        />
    </div>
</template>
    
<script>
    // import components
    import ImageGrid from "./ImageGrid.vue";
    import Featured from "./Featured.vue";
    
    export default {
        name: "Content",
        components: {
            ImageGrid,
            Featured
        },
        data() {
            return {
                featured: null
            }
        },
        methods: {},
        // receive images from parent
        props: ['images']
    }
</script>
    
<style>
</style>