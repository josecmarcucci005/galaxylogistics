<template>
  <div>
    <button class="ui medium primary button" v-on:click="displayAddModal()">
      <i class="plus icon" />
      Add Category
    </button>
    <br/><br/>
    <div class="ui icon input">
      <input type="text" placeholder="Search Category..." />
      <i class="search link icon"></i>
    </div>
    <table slot="content" class="ui celled striped table">
      <thead>
        <tr>
          <th>Category</th>
          <th>Description</th>
          <th class="left aligned four wide">Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="content in tableContent" :key="content.id">
          <td>{{ content.category }}</td>
          <td>{{ content.description }}</td>
          <td>
            <button
              class="ui small yellow button"
              v-on:click="displayUpdateModal(content)"
            >
              Edit
            </button>
            <button
              class="ui small red button"
              v-on:click="displayDeleteModal(content)"
            >
              Delete
            </button>
          </td>
        </tr>
      </tbody>
    </table>
    <ModalCategory
      v-if="showUpdateModal"
      v-bind="{ info: info, modalType: 'EDIT' }"
    ></ModalCategory>
    <ModalCategory
      v-if="showAddModal"
      v-bind="{ info: info, modalType: 'ADD' }"
    ></ModalCategory>
    <ModalDelete
      v-if="showDeleteModal"
      v-bind="{ customDeleteMsg: customDeleteMsg }"
    ></ModalDelete>

  </div>
</template>

<script>
import ModalCategory from "./ModalCategory.vue";
import ModalDelete from "./ModalDelete.vue";

export default {
  name: "manage-category",
  data() {
    return {
      tableContent: [
        { category: "Food", description: "Food Category" },
        { category: "Cloth", description: "Cloth Category" },
        { category: "Cosmetic", description: "Cosmetic Category" },
        { category: "Medicine", description: "Medicine Category" },
        { category: "Electronic", description: "Electronic Category" },
      ],
      showUpdateModal: false,
      showAddModal: false,
      showDeleteModal: false,
      info: {},
      customDeleteMsg : ""
    };
  },
  components: {
    ModalCategory,
    ModalDelete
  },
  methods: {
    displayUpdateModal: function (info) {
      this.showUpdateModal = true;
      this.info = info;
    },
    displayAddModal: function () {
      this.showAddModal = true;
      this.info = {};
    },
    displayDeleteModal: function (info) {
      this.showDeleteModal = true;
      this.customDeleteMsg = "Are you sure you want to delete the category '" + info.category + "' ?" ;
    }
  },
  mounted: function () {
    this.$root.$on("closeModalEvent", () => {
      this.showUpdateModal = false;
      this.showAddModal = false;
      this.showDeleteModal = false;
    });
  },
};
</script>

<style lang="scss">
</style>
