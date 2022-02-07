<template>
<v-container>
  <v-form ref="form" v-model="valid" lazy-validation>
    <v-select
      v-model="dataList.subject"
      :items="items1"
      :rules="[(v) => !!v || 'Item is required']"
      label="Subject"
      required
    ></v-select>

    <v-btn :disabled="!valid" color="success" class="mr-4" @click="save">
      submit
    </v-btn>
  </v-form>
  <v-card max-width="700" class="mx-auto">
    <v-toolbar color="indigo" dark>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>Inbox</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-toolbar>
    <v-list>
      <v-list-item v-for="(item,index) in List" :key="index">
        <v-list-item-content>
          <v-list-item-title v-text="item.name"></v-list-item-title>
        </v-list-item-content>
        <v-btn @click="Del(index)">Delete</v-btn>
      </v-list-item>
    </v-list>
  </v-card>
</v-container>
</template>

<script>
export default {
  data: () => ({
    valid: true,
    dataList: {
      subject: "",
    },
    List: [
      {
        name: "cs 1",
      },
    ],
    items1: ["cs 1", "cs 2", "cs 3", "cs 4"],
  }),
  methods: {
    save() {
      this.List.push({
        name: this.dataList.subject,
      });
    },
    Del(n){
        this.List.splice(n,1);
        }
  },
};
</script>

<style></style>
