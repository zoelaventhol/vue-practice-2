<!-- TEMPLATE 
    - This is the content we will see. 
    - We write it in HTML-->
<template>
    <div class="App">
        <div class ="Form">
            <h1>Picture time! 📸</h1>
            
            <!-- INPUT FORM -->
            <!-- button with @click to toggle showForm -->
            <button @click="showForm = !showForm">
                <!-- Conditionally change button text: if form is showing, button should say "Hide form" -->
                <p v-if="showForm">Hide form 🙈</p>
                <!-- Else (if form is hidden), should say "Add images!" -->
                <p v-else>Add images! 🖼️</p>
            </button>
            <!-- Add v-if to form, so it only renders when "showForm" is true -->
            <form v-if="showForm">
                Add image: 
                <!-- Add v-model to save input as a variable in data -->
                <input type="text" v-model="url"/>
                <br />
                <!-- Add @click event handler. ".prevent" to prevent the page refreshing. -->
                <button @click.prevent="addImage">Submit</button>
            </form>
        </div>

        <!-- IMAGE GRID PORTION-->
        <div class="ImageGrid">
            <!-- BIG & SMALL BUTTONS -->
            <div class = "buttons">
                <!-- Add click handlers to toggle "isBig" data -->
                <!-- Add conditional class "active": for Big when "isBig" is true, for Small when false -->
                <button @click="toggle(true)" :class="{ active: isBig }">Big</button>
                <button @click="toggle(false)" :class="{ active: !isBig }">Small</button>
            </div>
            <!-- IMAGES -->
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
    </div>
</template>
    
<!-- SCRIPTS 
    - These will add data and functionality to our app.
    - We write them in Javascript. -->
<script>
    // import component (by file path)

    export default {
        //  The name of our component. It should match the file name.
        name: 'App',
        // This is where we list any components we import.
        components: {
        },
        // This is where we create variables (in the return statement)
        data() {
            return {
                // Add variables to save url from input, and to save all image urls together
                url: "",
                images: [],
                showForm: false,
                isBig: false
            }
        },
        // This is where we define our functions.
        methods: {
            addImage() {
                // push image url into the images array
                this.images.push(this.url);
                // reset the form to blank
                this.url = "";
            },
            // toggle isBig true or false
            toggle(state) {
                this.isBig = state
            }
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