<template>
  <va-show-layout>
    <va-show :item="item">
      <!-- VaFields -->
    </va-show>
    <base-material-card
      :icon="$admin.getResource('comments').icon"
      :title="$admin.getResource('comments').pluralName"
    >
      <va-list
        resource="comments"
        disable-pagination
        disable-query-string
        :filter="{
          postId: id
        }"
      >
        <va-data-table :fields="fields" disable-select></va-data-table>
      </va-list>
    </base-material-card>
  </va-show-layout>
</template>

<script>
export default {
  props: ["id", "title", "item"],
  data() {
    return {
      fields: [
        { source: "name", sortable: true },
        { source: "email", type: "email" },
        "body"
      ]
    };
  }
};
</script>
