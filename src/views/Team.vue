<template>
  <div class="team">
    <v-container class="my-5">
    <h1 class="subheading grey--text">Team</h1>

      <v-row>
        <v-col  v-for="(person, i) in team" :key="i">
          <v-card dark>
            <!-- <v-avatar size="100"> -->
                <v-img :src="person.img" height="200px" />
            <!-- </v-avatar> -->
            <v-card-title>{{person.name}}</v-card-title>
            <v-card-text>{{person.role}}</v-card-text>

            <v-card-actions>
                <v-btn fab small style="background-color: #75CCFF;">
                    <v-icon>mdi-twitter</v-icon>
                </v-btn>
                <v-btn fab small style="background-color: #75CCFF;">
                    <v-icon>mdi-linkedin</v-icon>
                </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: 'Team',
  data () {
    return {
      team: [
        { name: 'Tochy', role: 'Fullstack Developer', img: 'https://images.pexels.com/photos/874158/pexels-photo-874158.jpeg?auto=compress&cs=tinysrgb&w=400' },
        { name: 'Chinex', role: 'Frontend Developer', img: 'https://images.pexels.com/photos/1222271/pexels-photo-1222271.jpeg?auto=compress&cs=tinysrgb&w=400' },
        { name: 'Obinna', role: 'Product Designer', img: 'https://images.pexels.com/photos/1121796/pexels-photo-1121796.jpeg?auto=compress&cs=tinysrgb&w=400' },
        { name: 'Pinocchio', role: 'Backend Developer', img: 'https://images.pexels.com/photos/91227/pexels-photo-91227.jpeg?auto=compress&cs=tinysrgb&w=400' }
      ]
    }
  }
}
</script>
