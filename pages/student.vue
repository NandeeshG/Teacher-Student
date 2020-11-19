<template>
  <v-app>
    <v-main>
      <v-container>
        <v-row justify="space-around">
          <v-col cols="9">
            <h1 class="text-h3 font-italic text-left mb-4">Students</h1>
            <v-form ref="form" class="mt-13" @submit.prevent="addStudent">
              <v-row justify="center">
                <v-col cols="12" sm="6">
                  <v-text-field
                    v-model="newStudent.name"
                    :rules="[rules.required, rules.name]"
                    dense
                    outlined
                    label="Name"
                    class="ma-n2"
                  />
                </v-col>
                <v-col cols="12" sm="6">
                  <v-text-field
                    v-model="newStudent.roll"
                    :rules="[rules.required, rules.roll]"
                    dense
                    outlined
                    label="Roll No."
                    class="ma-n2"
                  />
                </v-col>
                <v-col cols="12" sm="6">
                  <v-text-field
                    v-model="newStudent.class"
                    :rules="[rules.required, rules.class]"
                    dense
                    outlined
                    label="Class"
                    class="ma-n2"
                  />
                </v-col>
                <v-col cols="12" sm="6">
                  <v-text-field
                    v-model="newStudent.section"
                    :rules="[rules.required, rules.section]"
                    dense
                    outlined
                    label="Section"
                    class="ma-n2"
                  />
                </v-col>
              </v-row>
              <v-row justify="center">
                <v-col cols="12" sm="8">
                  <v-btn block type="submit"> ADD STUDENT </v-btn>
                </v-col>
              </v-row>
            </v-form>
          </v-col>
          <v-col cols="3">
            <v-img
              src="/students.png"
              width="300"
              height="500"
              transition="slide-y-transition"
            />
          </v-col>
        </v-row>

        <v-list three-line>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title> STUDENT-A </v-list-item-title>
              <v-list-item-subtitle> DETAILS </v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
        </v-list>

        <v-snackbar
          v-model="addedSuccessfuly"
          top
          transition="slide-y-transition"
          timeout="1000"
          color="green"
        >
          Success!
        </v-snackbar>
        <v-snackbar
          v-model="recheckInput"
          top
          transition="slide-y-transition"
          timeout="1000"
          color="red"
        >
          Please recheck input.
        </v-snackbar>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
/* eslint-disable no-console */
export default {
  data() {
    return {
      newStudent: {
        name: '',
        roll: '',
        section: '',
        class: '',
      },
      rules: {
        required: (value) => !!value || 'Required',
        name: (value) => {
          if (value === undefined || value.length <= 2 || value.length > 30)
            return 'Name should be between 3 and 30 characters'
          else {
            const pattern = /^[a-zA-Z]+[a-zA-Z\s-'.]*$/
            return !!pattern.test(value) || 'Invalid characters in name'
          }
        },
        roll: (value) => {
          const pattern = /^[1-9][0-9]*$/
          return (
            !!pattern.test(value) ||
            'Only numbers not starting with zero allowed'
          )
        },
        class: (value) => {
          const pattern = /^[1-9][0-2]*$/
          if (!pattern.test(value)) return 'Class invalid'
          else return true
        },
        section: (value) => {
          const pattern = /^[A-Z]$/
          if (!pattern.test(value))
            return 'Only single uppercase letters please'
          else if (value[0] < 'A' || value[0] > 'F') return 'Section invalid'
          else return true
        },
      },
      addedSuccessfuly: false,
      recheckInput: false,
    }
  },
  methods: {
    addStudent() {
      if (this.$refs.form.validate()) {
        this.addedSuccessfuly = true
      } else {
        this.recheckInput = true
      }
    },
  },
}
</script>

<style></style>
