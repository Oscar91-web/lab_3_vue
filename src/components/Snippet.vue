<template>
<div class="snipp">
  <div class="output">
    <div class="title">{{item.title}} 
        <div class="score">Score: {{item.score}}</div>
    </div> 
    
    <!-- ID: {{item.id}} <br/>  -->
    <div class="content">{{item.content}}</div>
    
  </div>
  <div class="buttons">
    <button @click="upvote">Upvote</button>
    <button @click="downvote">Downvote</button>
    <button @click="report">Report</button>
    <button @click="remove">Delete</button>
   

  </div>
</div>
</template>


<script>

const baseUrl= "https://www.forverkliga.se/JavaScript/api/api-snippets.php";

export default {
  name: 'Snippet',
  components: {

  },
  props: ['item'],
  methods: {
            async upvote() {
			try {
                console.log("getting data");
				let response = await this.$http.post(baseUrl,{
          id: this.item.id,
          upvote: ""
        });

                console.log(response.data);
			} catch(error) {
				console.log('Something went wrong', error);
			}
    },
    async report() {
			try {
                console.log("getting data");
				let response = await this.$http.post(baseUrl,{
          id: this.item.id,
          report: ""
        });
	
                console.log(response.data);
			} catch(error) {
				console.log('Something went wrong', error);
			}
    },
    async remove() {
			try {
                console.log("getting data");
				let response = await this.$http.post(baseUrl,{
          id: this.item.id,
          delete: ""
        });

                console.log(response.data);
			} catch(error) {
				console.log('Something went wrong', error);
			}
    },
    async downvote() {
			try {
                console.log("getting data");
				let response = await this.$http.post(baseUrl,{
          id: this.item.id,
          downvote: ""
        });

                console.log(response.data);
			} catch(error) {
				console.log('Something went wrong', error);
			}
    }
  }
}
//     is_reported: response.data.is_reported,
</script>
<style scoped>
   .snipp{
        display: grid;
        grid-template-columns: 1fr auto;
        grid-template-rows: auto;
        border: 3px inset white;
        padding: 0px;
        grid-template-areas: 
        "output output buttons";
        white-space: pre;  
    }
    .title{
      background-color: #404040;
      border-bottom: 3px inset white;
      font-size: 1.2em;
      padding: 2px;
    }
    .content{
      overflow:auto; 
      max-height:20em;
    }
    .score{
      float: right;
      background-color: transparent;
    }
    .buttons{
      display: inherit;
    }

</style>

