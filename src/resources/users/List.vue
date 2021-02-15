<template>
  <div>
    <va-aside-layout :title="asideTitle">
      <users-show v-if="show" :item="item"></users-show>
      <users-form v-else :id="id" :item="item" @saved="onSaved"></users-form>
    </va-aside-layout>
    <base-material-card :icon="resource.icon" :title="title">
      <va-list ref="list" disable-create-redirect @action="onAction">
        <va-data-table
          :fields="fields"
          disable-create-redirect
          disable-show-redirect
          disable-edit-redirect
          @item-action="onAction"
        >
          <template v-slot:[`field.address`]="{ value }">
            {{ value.street }} {{ value.suite }} {{ value.city }}
          </template>
        </va-data-table>
      </va-list>
    </base-material-card>
  </div>
</template>

<script>
export default {
  props: ["resource", "title"],
  data() {
    return {
      fields: [
        { source: "id", sortable: true },
        { source: "name", sortable: true },
        { source: "username", sortable: true },
        { source: "email", type: "email" },
        //{ source: "address", type: "address" }, //custom field
        "address",
        "phone",
        { source: "website", type: "url" },
        "company.name"
      ],
      asideTitle: null,
      id: null,
      item: null,
      show: false
    };
  },
  methods: {
    async onAction({ action, title, id, item }) {
      this.asideTitle = title;
      this.id = id;
      this.show = action === "show";
      this.item = item;
    },
    onSaved() {
      this.asideTitle = null;
      this.$refs.list.fetchData();
    }
  }
};
</script>
