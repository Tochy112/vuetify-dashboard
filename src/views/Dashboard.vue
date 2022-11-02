<template>
  <div class="dashboard mx-4">
    <v-container>
      <h1 class="subheading grey--text mb-3">Dashboard</h1>

      <v-row class="mb-3">
        <v-col>
          <v-tooltip top>
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                class="caption" @click="sortBy('title')"
                v-bind="attrs"
                v-on="on"
              >
              <v-icon left small>mdi-folder</v-icon>
                  Sort by title
              </v-btn>
            </template>
            <span>Sort task by project title</span>
          </v-tooltip>
        </v-col>

        <v-col>
          <v-tooltip top>
            <template v-slot:activator="{ on, attrs }">
              <v-btn
                class="caption" @click="sortBy('Person')"
                v-bind="attrs"
                v-on="on"
              >
              <v-icon left small>mdi-book</v-icon>
              Sort by person
              </v-btn>
            </template>
            <span>Sort task by name</span>
          </v-tooltip>
        </v-col>
      </v-row>

      <v-card flat class="pa-3 " v-for="(project, i) in projects" :key="i">
        <v-row row wrap :class="`pa-3 project ${project.status}`">
          <v-col xs12 md6>
            <div class="caption grey--text">Project title</div>
            <div>{{project.title}}</div>
          </v-col>

          <v-col xs6 sm4 md2>
            <div class="caption grey--text">Person</div>
            <div>{{project.Person}}</div>
          </v-col>

          <v-col xs6 sm4 md2>
            <div class="caption grey--text">Due by</div>
            <div>{{project.Due}}</div>
          </v-col>

          <v-col xs2 sm4 md2>
            <div>
              <v-chip close-icon="mdi-close-outline" :class="`${project.status} caption`" label outlined>
                {{ project.status }}
              </v-chip>
            </div>
          </v-col>
        </v-row>

        <v-divider></v-divider>

      </v-card>
    </v-container>
  </div>
</template>

<script>
export default {
  name: 'Dashboard',

  data () {
    return {
      projects: this.projects
    }
  },
  methods: {
    sortBy (prop) {
      this.projects.sort((a, b) => a[prop] < b[prop] ? -1 : 1)
    }
  },

  created () {
    this.projects = [
      { title: 'Github lessons for trainees', Person: 'Tochy', Due: '27/10/22', status: 'Ongoing' },
      { title: 'Build an API', Person: 'Chinex', Due: '26/10/22', status: 'Complete' },
      { title: 'landing page UI', Person: 'Obinna', Due: '26/10/22', status: 'Overdue' },
      { title: 'NodeJs live session', Person: 'Odira', Due: '25/10/22', status: 'Complete' }
    ]
  }
}
</script>

<style scoped>
.project.Complete{
  border-left: 4px solid green;
}
.project.Ongoing{
  border-left: 4px solid gold;
}
.project.Overdue{
  border-left: 4px solid orangered;
}
.v-chip.Complete{
  border-color:green;
}
.v-chip.Ongoing{
  border-color:gold;
}
.v-chip.Overdue{
  border-color:orangered;
}
</style>
