<template>
  <div class="project mx-4">
    <v-container class="my-5">
      <h1 class="subheading grey--text mb-4">Projects</h1>

      <v-expansion-panels>
        <v-expansion-panel v-for="(project, i) in  myProject" :key="i">
          <v-expansion-panel-header>
            {{ project.title }}
          </v-expansion-panel-header>
          <v-expansion-panel-content class="grey--text">
            <div class="mb-3">Due by {{ project.Due }}</div>
            <div>{{project.content}}</div>
          </v-expansion-panel-content>
        </v-expansion-panel>
      </v-expansion-panels>
    </v-container>
  </div>
</template>

<script>
export default {
  name: 'Project',
  data () {
    return {
      projects: [
        { title: 'Github lessons for trainees', Person: 'Tochy', Due: '27/10/22', content: 'Lorem ipsum it habit commet et' },
        { title: 'Build an API', Person: 'Chinex', Due: '26/10/22', content: 'Lorem ipsum it habit commet et' },
        { title: 'landing page UI', Person: 'Obinna', Due: '26/10/22', content: 'Lorem ipsum it habit commet et' },
        { title: 'NodeJs live session', Person: 'Odira', Due: '25/10/22', content: 'Lorem ipsum it habit commet et' },
        { title: 'Laravel live session', Person: 'Chinex', Due: '30/10/22', content: 'Lorem ipsum it habit commet et' }
      ]
    }
  },
  computed: {
    myProject () {
      return this.projects.filter((project) => {
        return project.Person === 'Chinex'
      })
    }
  }
}
</script>
