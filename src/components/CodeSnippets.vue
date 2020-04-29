<template>
    <div class="start"><!-- rör mig inte -->
        <div>
            <div class="butts">
                <button @click="getLatest">Latest</button>
                <button @click="getBest">Best</button>
            </div>
            <div class=loading
            v-show="loading">Loading...</div>
            <div class="CodeSnippets">
                <snippet v-for="item in model"
                    v-bind:item="item"
                    v-bind:key="item.id">
                </snippet>
            </div>
        </div>
        <div class="chill">
            <add></add>
        </div>
    </div> <!-- rör mig inte -->
</template>

<script>
const baseUrl = "https://www.forverkliga.se/JavaScript/api/api-snippets.php?";

import Snippet from './Snippet'
import AddSnippet from './AddSnippet'
export default {
    components:{
        "snippet": Snippet,
        "add": AddSnippet
    },
    data: () => ({
        model: null,
        loading: false
        
    }),
    methods:{
        async getLatest() {
			try {
                console.log("getting data");
                this.loading=true;
				let response = await this.$http.get(baseUrl +"latest");
				this.loading=false;
                console.log('done');
                console.log(response.data);
                this.model=response.data;
                console.log(this.model)
			} catch(error) {
				console.log('Something went wrong', error);
			}
        },
        async getBest() {
			try {
                this.loading=true;
                console.log("getting data");
				let response = await this.$http.get(baseUrl + "best");
				this.loading=false;
                console.log('done');
                console.log(response.data);
                this.model=response.data;
                console.log(this.model)
			} catch(error) {
				console.log('Something went wrong', error);
			}
		}
    }

}
</script>

<style>
    .chill{
        position: -webkit-sticky;
        position:sticky;
        top: 20px;
        height: 20em;
        
    }
    .start{
        max-width: 70em;
        padding: 10px;
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 2em;
        margin: 10px auto 0 auto;
    }
    .CodeSnippets{
        display: grid;
        grid-template-columns: 1fr;
        grid-template-rows: auto;
        grid-gap: 20px;
        
    }
    .butts{
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-template-rows: auto;
    }

</style>