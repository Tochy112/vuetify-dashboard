<template>
  <div class="text-center">
    <v-dialog v-model="dialog" width="600">
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="success lighten-1"
          dark
          depressed
          v-bind="attrs"
          v-on="on"
        >
          Add task

          <v-icon right>mdi-plus</v-icon>
        </v-btn>
      </template>

      <v-card>
        <v-card-title class="text-h5 grey lighten-2">
          Add a new project
        </v-card-title>

        <v-card-text>
          <v-form ref="form">
            <v-text-field
              label="Title"
              v-model="formInputs.title"
              prepend-icon="mdi-folder"
              :rules="inputRules"
            ></v-text-field>
            <v-textarea
              label="Information"
              v-model="formInputs.content"
              prepend-icon="mdi-pencil"
              :rules="inputRules"
            ></v-textarea>

            <!-- date picker -->
            <v-dialog
              ref="dialog"
              v-model="modal"
              :return-value.sync="date"
              persistent
              width="290px"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-text-field
                  v-model="date"
                  label="Pick a date"
                  prepend-icon="mdi-calendar"
                  readonly
                  v-bind="attrs"
                  v-on="on"
                  :rules="dateRules"
                ></v-text-field>
              </template>
              <v-date-picker v-model="date" scrollable>
                <v-spacer></v-spacer>
                <v-btn text color="primary" @click="modal = false">
                  Cancel
                </v-btn>
                <v-btn text color="primary" @click="$refs.dialog.save(date)">
                  OK
                </v-btn>
              </v-date-picker>
            </v-dialog>
            <!-- button -->
            <v-btn color="success lighten-1" @click="handleSubmit" :loading="loading">Add</v-btn>
          </v-form>
        </v-card-text>

        <v-divider></v-divider>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
  name: 'popUp',
  data () {
    return {
      dialog: false,
      modal: false,
      date: null,
      formInputs: {
        title: '',
        content: ''
      },
      loading: false,
      // showSnackBar: true,
      inputRules: [
        v => !!v || "Field can't be empty",
        v => v.length >= 5 || 'Minimum of five characters'
      ],
      dateRules: [
        v => !!v || 'Choose a date'
      ]
    }
  },
  methods: {
    handleSubmit () {
      if (this.$refs.form.validate()) {
        this.loading = true
        console.log(this.formInputs.title, this.formInputs.content, this.date)

        setTimeout(() => {
          this.loading = false
        }, 1500)

        this.$refs.form.reset()

        this.$emit(this.projectAdded)
      }
    }
  }
}
</script>
