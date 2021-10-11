<template>
    <div>
        <b-card-group columns>
            <b-card
                v-for="giph in giphs"
                :key = "giph.id"
                :img-src="giph.images.fixed_height.url"
                :img-alt="giph.title"
            >
                <b-card-text>
                    <a :href="giph.url" target="blank">{{giph.title}}</a>
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
    .card {
        margin-bottom: 2rem;
    }
    @media (min-width: 34em) {
    .card-columns {
        -webkit-column-count: 2;
        -moz-column-count: 2;
        column-count: 2;
    }
}
@media (min-width: 48em) {
    .card-columns {
        -webkit-column-count: 3;
        -moz-column-count: 3;
        column-count: 3;
    }
}
@media (min-width: 62em) {
    .card-columns {
        -webkit-column-count: 4;
        -moz-column-count: 4;
        column-count: 4;
    }
}
@media (min-width: 75em) {
    .card-columns {
        -webkit-column-count: 5;
        -moz-column-count: 5;
        column-count: 5;
    }
}  

</style>
