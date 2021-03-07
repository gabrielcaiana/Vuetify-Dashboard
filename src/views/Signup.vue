<template>
  <v-container>
    <v-row>
      <v-col>
        <h1>Signup</h1>
        <v-form @submit.prevent="submit">
          <v-text-field label="Email" type="Email"> </v-text-field>
          <v-autocomplete
            label="witch browser do you use?"
            :items="browsers"
          ></v-autocomplete>
          <v-file-input label="Attach profile picture"></v-file-input>

          <v-dialog
            ref="dialog"
            v-model="modal"
            :return-value.sync="date"
            persistent
            width="290px"
          >
            <template v-slot:activator="{ on, attrs }">
              <v-text-field
                v-model="birthday"
                label="Birthday"
                prepend-icon="mdi-calendar"
                readonly
                v-bind="attrs"
                v-on="on"
              ></v-text-field>
            </template>
            <v-date-picker v-model="birthday" scrollable>
              <v-spacer></v-spacer>
              <v-btn text color="primary" @click="modal = false">
                Cancel
              </v-btn>
              <v-btn text color="primary" @click="$refs.dialog.save(birthday)">
                OK
              </v-btn>
            </v-date-picker>
          </v-dialog>

          <v-checkbox label="Agree to terms & conditions"></v-checkbox>
          <v-btn type="submit" color="primary">Submit</v-btn>
        </v-form>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    browsers: ["Chrome", "Firefox", "Safari", "Edge", "Brave"],
    birthday: "",
    modal: false,
  }),

  methods: {
    submit() {
      alert("Hello world");
    },
  },
};
</script>

<style lang="scss" scoped></style>
