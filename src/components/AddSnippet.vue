<template>
<div class=start1>
  <div class="inputs">
        <div class="title">
            <label>Title: </label>
            <input type="text" 
            placeholder="title" 
            v-model="model.title"/>
            
        </div>
        
        <div class="content">
            <label>Content: </label>
            <textarea 
                type="text"
                placeholder="content"
                v-model="model.content"/>
        </div> 
        <div class="loader"
            v-show= "loading">
            Saving...
        </div>
        <div class="add"><button @click="add">Add</button></div>
  </div>
  
</div>
  
</template>


<script>

const baseUrl= "https://www.forverkliga.se/JavaScript/api/api-snippets.php";
export default {
  name: 'AddSnippet',
  components: {
    
  },
  data: () => ({
      model: {
          title: "",
          content: ""   
      },
      loading: false 
  }),

  methods: {
            async add() {
			try {
                console.log("getting data");
                this.loading= true;
				let response = await this.$http.post(baseUrl,{
                    title: this.model.title,
                    content: this.model.content,
                    add: ""
        });
					
        this.model.title= "";
        this.model.content="";
        this.loading=false;
        console.log('done');
        console.log(response.data);
        } catch(error) {
            console.log('Something went wrong', error);
        }
    }
  }
}
</script>
<style scoped>
    .start1{
        border: 3px inset white;
        padding: 10px;
    }
   .inputs{
        display: grid;
        grid-gap: 10px;
        grid-template-columns: 1fr 1fr;
        grid-template-rows: auto auto auto;
        grid-template-areas:
        "title title"
        "content content" 
        ". add" 
    }
    .title{grid-area: title}
    .tags{grid-area: tags}
    .content{grid-area: content}
    .add{grid-area: add}
    button{float: right}
    input, textarea{width: 100%}
    textarea{height: 10em}   
</style>

