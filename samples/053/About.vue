<template>
  <div class="content">
    <v-row>
      <v-col cols="5">
        <div style="position: relative" class="mt-16">
          <h1 class="text-grey">My, My Self & I</h1>
        
          <p>I'm a Frontend developer located in Turkey. I have a serious passion for UI effects, animations
            and creating intuitive, dynamic user experiences.
          </p><br>
          <p>Well orginased person, problem solver , Fan of Fashion, outdoor activities, TV series and French literature.
            A family person.
          </p><br>
          <p>Interested in the entire frontend spectrum and working on ambitious projects with positive people.</p><br>
          <h1>My skills</h1>
          <h5>-Javascript</h5>
          <h5>-Typescript</h5>
          <h5>-Html</h5>
          <h5>-Css</h5>
          <h5>-React js</h5>
          <h5>-Vue js</h5>
          
        </div>
      </v-col>
      <v-col cols="7">
            <div style=" position:absolute, z-index: 9999; " class="mt-16">
              <v-img
               class="image"
                src="https://images.unsplash.com/photo-1610986603166-f78428624e76?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=858&q=80"
                contain
                max-height="300"
              ></v-img>
            </div>
          </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: "AboutVue",
};
</script>
<style scoped>
.content {
  background: black;
  width: 100%;
  height: 100vh;
  padding-left: 20px;
  color : white;
}
.image{
    border-radius: 50%;
}
</style>
>
