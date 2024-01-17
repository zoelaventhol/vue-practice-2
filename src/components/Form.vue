<template>
    <div class="Form">
        Add image: 
        <!-- Add v-model to save input as a variable in data -->
        <input type="text" v-model="url"/>
        <br />
        <!-- Add @click event handler. ".prevent" to prevent the page refreshing. -->
        <button @click.prevent="handleSubmit">Submit</button>
    </div>
</template>
    
<script>
    export default {
        name: 'Form',
        components: {},
        data() {
            return {
                // Add variable to save url from input
                url: "",
            }
        },
        methods: {
            // this will run when "Submit" button is clicked
            handleSubmit() {
                // emit URL to parent with event title "submitted"
                this.$emit("submitted", this.url);
                // reset URL/input to blank
                this.url = ""
            }
        },
        // It's good practice to define your emits, but it's not necessary
        emits: ["submitted"],
        props: []
    }
</script>
    
<style>
</style>