<template>
    <div>
        <b-card-group deck>
            <b-card
                v-for="giph in giphs"
                :key = "giph.id"
                :img-src="giph.images.fixed_height.url"
                :img-alt="giph.title"
            >
                <b-card-text>
                    <a :href="giph.url">target="blank">{{giph.title}}</a>
                </b-card-text>   
            </b-card>    
        </b-card-group>   
              
    </div>   
    
</template>
<script>
    import axios from 'axios';
    const GIPHY_URL = "https://api.giphy.com/v1/gifs";
    const API_KEY = "w9BFuBe60HUqJpXePQv94dA8SXuTQkp1";
    export default {
        name: 'GiphyViewer',
        data() {
            return {
                giphs: []
            };
        },
        mounted() {
            axios.get(`${GIPHY_URL}/trending?api_key=${API_KEY}`)
                 .then(response => {
                     console.log(response.data.data)
                     this.giphs = response.data.data
                 })
                 .catch(error => console.log(error))      
        },
        methods: {
        }
    }
</script>
<style>

</style>
