<!-- TEMPLATE 
    - This is the content we will see. 
    - We write it in HTML-->
<template>
    <div class="App">
        <h1>Picture time! 📸</h1>

        <button @click="showForm = !showForm">
            <p v-if="showForm">Hide form</p>
            <p v-else>Add images!</p>
        </button>
        
        <!-- INPUT FORM -->
        <form v-if="showForm">
            <Form @submitted="(url) => addImage(url)"/>
        </form>

        <!-- CONTENT: Featured image & image grid. Pass images as a prop -->
        <Content :images="images" />
    </div>
</template>
    
<!-- SCRIPTS 
    - These will add data and functionality to our app.
    - We write them in Javascript. -->
<script>
    // import components (by file path)
    import ImageGrid from "./components/ImageGrid.vue";
    import Form from "./components/Form.vue";
    import Content from "./components/Content.vue";

    export default {
        //  The name of our component. It should match the file name.
        name: 'App',
        // This is where we list any components we import.
        components: {
            ImageGrid,
            Form, 
            Content
        },
        data() {
            return {
                // Remove url variable (it's now in Form.vue instead)
                images: ["https://cdn.pixabay.com/photo/2024/01/07/16/27/reed-8493547_1280.jpg"],
                showForm: false
            }
        },
        methods: {
            // update addImage to accept URL as a parameter
            addImage(url) {
                // change from this.url to just url (aka the url received as a parameter)
                this.images.push(url);
            },
 
        }
    }
</script>
    
<!-- STYLES
    - These will add style and formatting to our content.
    - We write it in CSS -->
<style>
    .App {
        margin: 0 auto;
        font-family: Arial, Helvetica, sans-serif;
        text-align: center;
    }

    input, button {
        margin-bottom: 2em;
    }

    button {
        border-radius: 5px
    }

    .image-grid {
        /* set it up as a grid with 3 columns, and a gap between images */
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        gap: 1em;
        
        /* center it on the page */
        width: 50%;
        margin: auto;
    }

    img {
        /* standardize height */
        height: 150px;
        /* make everything square */
        aspect-ratio: 1;
        /* make sure image is cropped, not distorted */
        object-fit: cover;
        /* round the corners */
        border-radius: 10%;
    }
</style>