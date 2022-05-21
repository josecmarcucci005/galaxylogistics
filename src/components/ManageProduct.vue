<template>
  <div>
    <button class="ui medium primary button" v-on:click="displayAddModal()">
      <i class="plus icon" />
      Add Product
    </button>
    <br/><br/>
    <div class="ui icon input">
      <input type="text" placeholder="Search Product..." />
      <i class="search link icon"></i>
    </div>
    <table slot="content" class="ui celled striped table">
      <thead>
        <tr>
          <th>Product</th>
          <th>Category</th>
          <th>Inventory</th>
          <th class="left aligned four wide">Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="content in tableContent" :key="content.id">
          <td>{{ content.name }}</td>
          <td>{{ content.category }}</td>
          <td>{{ content.inventory }}</td>
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
    <ModalProduct
      v-if="showUpdateModal"
      v-bind="{ info: info, modalType: 'EDIT' }"
    ></ModalProduct>
    <ModalProduct
      v-if="showAddModal"
      v-bind="{ info: info, modalType: 'ADD' }"
    ></ModalProduct>
    <ModalDelete
      v-if="showDeleteModal"
      v-bind="{ customDeleteMsg: customDeleteMsg }"
    ></ModalDelete>

  </div>
</template>

<script>
import ModalProduct from "./ModalProduct.vue";
import ModalDelete from "./ModalDelete.vue";

export default {
  name: "manage-product",
  data() {
    return {
      tableContent: [
        { name: "Banana ", category: "Food", inventory: 1000 },
        { name: "Apples ", category: "Food", inventory: 1000 },
        { name: "Air Jordan Shoes ", category: "Cloth", inventory: 79 },
        { name: "Gatorade ", category: "Food", inventory: 678 },
        { name: "Coca=Cola ", category: "Food", inventory: 854 }
      ],
      showUpdateModal: false,
      showAddModal: false,
      showDeleteModal: false,
      info: {},
      customDeleteMsg : ""
    };
  },
  components: {
    ModalProduct,
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
      this.customDeleteMsg = "Are you sure you want to delete the product '" + info.name + "' ?" ;
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
