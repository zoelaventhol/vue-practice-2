<template>
    <div class="ImageGrid">
        <!-- BUTTONS -->
        <div class = "buttons">
            <!-- Add click handlers to toggle "isBig" data -->
            <!-- Add conditional class "active": for Big when "isBig" is true, for Small when false -->
            <button @click="toggle(true)" :class="{ active: isBig }">Big</button>
            <button @click="toggle(false)" :class="{ active: !isBig }">Small</button>
        </div>
        <!-- IMAGE GRID -->
        <div class = "image-grid">
            <!-- Create an <img> tag for each of your URLs using a v-for loop. Set your URL as the src attribute. -->
            <!-- Add conditional class "big" when "isBig" is true -->
            <img 
                v-for="url in images" 
                :src = "url"
                :class="{ big: isBig }"
            />

        </div>
    </div>
</template>
    
<script>
    export default {
        name: 'ImageGrid',
        components: {},
        data() {
            return {
                isBig: false
            }
        },
        methods: {
            // toggle isBig true or false
            toggle(state) {
                this.isBig = state
                console.log("isBig: ", this.isBig)
            }
        },
        // receive props
        props: ['images']
    }
</script>
    
<style>
    .buttons {
        display: flex;
        width:50%;
        margin: auto;
        justify-content: left;
        gap: 1em;
    }

    /* Create "active" class */
    .active {
        color: red;
        border: 2px solid red;
    }

    /* Create "big" class */
    .big {
        height: 200px;
    }
</style>