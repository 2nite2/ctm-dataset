<template>
   
    <div class="container">
      <h1 class="titre">Our Projects with React js & Vue js</h1>
  <v-row justify="center"  class="space px-16 ">
    <v-col
      cols="12"
      xs="12"
      sm="6"
      md="4"
      v-for="(project, i) in Projects"
      :key="i"
      style="cursor: pointer"
    >
      <v-card class="mx-auto" max-width="344">
        <v-img :src="project.img" height="100%" width="100%"></v-img>

        <v-card-title>
          {{ project.name }}
        </v-card-title>
        <v-spacer></v-spacer>
        <v-card-actions>

          <v-btn @click="handleClick(project.link)" color="orange lighten-2" text>See Project </v-btn>

        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</div>
</template>

<script>

export default {
    name: "ProJect",
    data() {
        return {
            Projects: [
                {
                    id: 1,
                    name: "Real estate",
                    img: "https://images.unsplash.com/photo-1560518883-ce09059eeffa?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=773&q=80",
                    link: "https://github.com/fouziabenadida/real-estate-project",
                },
                {
                    id: 2,
                    name: "e-commerce App",
                    img: "https://images.unsplash.com/photo-1605902711622-cfb43c4437b5?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=869&q=80",
                    link: "https://github.com/fouziabenadida/simple-e-commerce-app",
                },
                {
                    id: 3,
                    name: "food-delivery App",
                    img: "https://images.unsplash.com/photo-1600728619239-d2a73f7aa541?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=870&q=80",
                    link: "https://github.com/fouziabenadida/weather-app-vuejs2",
                },
                {
                    id: 4,
                    name: "Weather App",
                    img: "https://images.unsplash.com/photo-1530563885674-66db50a1af19?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=869&q=80",
                    link: "https://github.com/fouziabenadida/weather-app-vuejs2",
                },
                {
                    id: 5,
                    name: "Todo-List- Vuejs",
                    img: "https://images.unsplash.com/photo-1484480974693-6ca0a78fb36b?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=872&q=80",
                    link: "https://github.com/fouziabenadida/todo-list-vuejs2",
                },
                {
                    id: 6,
                    name: "Portfolio vue 3",
                    img: "https://images.unsplash.com/photo-1487611459768-bd414656ea10?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=870&q=80",
                    link: "https://github.com/fouziabenadida/portfolio-vue3",
                },
            ],
        };
    },
    methods: {
    handleClick(link) {
      window.location.href = link
    }
    },
    components: {  }
};
</script>

<style scoped>
.container{
  padding: 10px;
}
.titre{
  text-align: center;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
  font-size: 18px;
  font-weight: 800;
  padding: 20px;
}
</style>>


