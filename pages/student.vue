<template>
  <v-app>
    <v-main>
      <v-container>
        <v-row justify="space-around">
          <v-col cols="9">
            <h1 class="text-h3 font-italic text-left mb-4">Students</h1>
            <v-form class="mt-13">
              <v-row justify="center">
                <v-col cols="12" sm="6">
                  <v-text-field dense outlined label="Name" class="ma-n2" />
                </v-col>
                <v-col cols="12" sm="6">
                  <v-text-field dense outlined label="Roll No." class="ma-n2" />
                </v-col>
                <v-col cols="12" sm="6">
                  <v-text-field dense outlined label="Class" class="ma-n2" />
                </v-col>
                <v-col cols="12" sm="6">
                  <v-text-field dense outlined label="Section" class="ma-n2" />
                </v-col>
              </v-row>
              <v-row justify="center">
                <v-col cols="12" sm="8">
                  <v-btn block> ADD STUDENT </v-btn>
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
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {}
</script>

<style></style>
