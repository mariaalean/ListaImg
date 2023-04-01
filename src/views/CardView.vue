<template>
  <!-- <div  class="d-flex align-content-center flex-wrap"> -->
    <v-row>
      <v-col cols="4"
      v-for="(item, index) in items" :key="index"> 
   
    
    <v-card
    class="mx-auto"
      max-width="344"
    >
      <v-img
        :src="item.download_url"
        height="200px"
        cover
      ></v-img>
  
      <v-card-title>
        {{item.author}}
      </v-card-title>
  
      <v-card-subtitle>
       {{item.id}}
      </v-card-subtitle>
  
      <v-card-actions>
        <RouterLink to="item.url">
          <v-btn
            color="orange-lighten-2"
            variant="text"
          >
            Explore
          </v-btn>
        </RouterLink>
        <v-spacer></v-spacer>
  
        <v-btn
          :icon="show ? 'mdi-chevron-up' : 'mdi-chevron-down'"
          @click="show = !show"
        ></v-btn>
      </v-card-actions>
  
      <v-expand-transition>
        <div v-show="show">
          <v-divider></v-divider>
  
          <v-card-text>
            height {{ item.height }} width {{ item.width }}
           </v-card-text>
        </div>
      </v-expand-transition>
    </v-card>
  </v-col>
    </v-row>
  <!-- </div> -->
  </template>
  
  <script>
    export default {
      data: () => ({
        show: false,
        items: []
      }),
      methods: {
        fetchData(){
            fetch('https://picsum.photos/v2/list?page=28&limit=12').then(response => response.json()).then(data=>{
              this.items=data
            })
           .catch(error => console.log(error));
          // console.log(this.items)
           }
       },
       created() {
            this.fetchData();
           },

      } 
  </script>

