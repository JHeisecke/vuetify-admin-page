<template>
  <v-card>
    <v-card-title>
      <h1 class="display-1">
        {{ title }}
      </h1>
    </v-card-title>
    <v-card-text>
      <base-material-card :icon="resource.icon" :title="title">
        <va-list>
          <va-data-table :fields="fields"></va-data-table>
        </va-list>
      </base-material-card>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  props: ["resource", "title"],
  data() {
    return {
      fields: ["title", "body"]
    };
  }
};
</script>
