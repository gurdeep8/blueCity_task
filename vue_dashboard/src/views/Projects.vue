<template>
  <div class="projects">
    <!-- <h1 class="subheading grey--text">My Task</h1> -->
    <v-container>
      <v-card flat v-for="project in projects" :key="project.title" class="mb-1">
        <v-layout row wrap :class="`pa-3 project ${project.status}`">
          <v-flex xs12 md6>
            <div class="caption grey--text">Project title</div>
            <div>{{project.title}}</div>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <div class="caption grey--text">Person</div>
            <div>{{project.person}}</div>
          </v-flex>
          <v-flex xs6 sm4 md2>
            <div class="caption grey--text">Due By</div>
            <div>{{project.due}}</div>
          </v-flex>
        </v-layout>
      </v-card>
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "projects",
  components: {},
  data: () => ({
    projects: [
      { title: "Collapsible Side menu",
       person: "Gurdeep Singh",
        due: "07/26/2020",
       status: "complete" 
       },
      {
        title: "Charts Visualization",
        person: "Gurdeep Singh",
        due: "07/26/2020",
        status: "complete",
      },
      {
        title: "Web Socket Data Visualization",
        person: "Gurdeep Singh",
        due: "07/26/2020",
        status: "complete",
      },
      {
        title: "Git-tree",
        person: "Gurdeep Singh",
        due: "07/26/2020",
        status: "yes",
      },
    ],
  }),
  
};
</script>
<style >
.project.complete {
  border-left: 4px solid #3cd1c2;
}
.project.yes{
  border-left:4px solid yellow;
}

</style>
