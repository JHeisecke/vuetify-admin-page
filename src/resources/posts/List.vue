<template>
  <v-card>
    <v-card-title>
      <h1 class="display-1">
        {{ title }}
      </h1>
    </v-card-title>
    <v-card-text>
      <base-material-card :icon="resource.icon" :title="title">
        <va-list :include="{ expand: ['user'] }" :filters="filters">
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
      filters: [
        {
          source: "userId",
          type: "select",
          alwaysOn: true,
          attributes: { reference: "users" }
        }
      ],
      fields: [
        {
          source: "user",
          type: "reference",
          attributes: { reference: "users", link: "edit", chip: true }
        },
        "title",
        "body"
      ]
    };
  }
};
</script>
