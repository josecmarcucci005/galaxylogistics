<template>
  <div>
    <div class="ui icon input">
      <input type="text" placeholder="Search Order..." />
      <i class="search link icon"></i>
    </div>
    <table slot="content" class="ui celled striped table">
      <thead>
        <tr>
          <th>Order Id</th>
          <th>Status</th>
          <th>Customer</th>
          <th class="left aligned four wide">Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="content in tableContent" :key="content.id">
          <td>
            <a v-on:click.prevent="displayViewModal(content)">{{
              content.orderId
            }}</a>
          </td>
          <td>{{ content.status }}</td>
          <td>{{ content.customer }}</td>
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
    <ModalOrders
      v-if="showUpdateModal"
      v-bind="{ info: info, modalType: 'EDIT' }"
    ></ModalOrders>
    <ModalOrders
      v-if="showViewModal"
      v-bind="{ info: info, modalType: 'VIEW' }"
    ></ModalOrders>
    <ModalDelete
      v-if="showDeleteModal"
      v-bind="{ customDeleteMsg: customDeleteMsg }"
    ></ModalDelete>
  </div>
</template>

<script>
import ModalOrders from "./ModalOrders.vue";
import ModalDelete from "./ModalDelete.vue";

export default {
  name: "manage-product",
  data() {
    return {
      tableContent: [
        {
          orderId: "1111",
          status: "Open",
          customer: "Magic Johnson",
          products: [
            { name: "Gatorade ", category: "Food", qty: 5 },
            { name: "Coca-Cola ", category: "Food", qty: 8 },
            { name: "Doritos ", category: "Food", qty: 3 },
          ],
          total: 16,
        },
        {
          orderId: "2222",
          status: "Cancelled",
          customer: "Denis Rodman",
          products: [
            { name: "Gatorade ", category: "Food", qty: 5 },
            { name: "Coca-Cola ", category: "Food", qty: 8 },
            { name: "Doritos ", category: "Food", qty: 3 },
          ],
          total: 16,
        },
        {
          orderId: "3333",
          status: "Processed",
          customer: "Michael Jordan",
          products: [
            { name: "Gatorade ", category: "Food", qty: 5 },
            { name: "Coca-Cola ", category: "Food", qty: 8 },
            { name: "Doritos ", category: "Food", qty: 3 },
          ],
          total: 16,
        },
        {
          orderId: "3333",
          status: "Delivered",
          customer: "Luka Doncic",
          products: [
            { name: "Gatorade ", category: "Food", qty: 5 },
            { name: "Coca-Cola ", category: "Food", qty: 8 },
            { name: "Doritos ", category: "Food", qty: 3 },
          ],
          total: 16,
        },
        {
          orderId: "3333",
          status: "Closed",
          customer: "Lebron James",
          products: [
            { name: "Gatorade ", category: "Food", qty: 5 },
            { name: "Coca-Cola ", category: "Food", qty: 8 },
            { name: "Doritos ", category: "Food", qty: 3 },
          ],
          total: 16,
        },
      ],
      showUpdateModal: false,
      showViewModal: false,
      showDeleteModal: false,
      info: {},
      customDeleteMsg: "",
    };
  },
  components: {
    ModalOrders,
    ModalDelete,
  },
  methods: {
    displayUpdateModal: function (info) {
      this.showUpdateModal = true;
      this.info = info;
    },
    displayViewModal: function (info) {
      this.showViewModal = true;
      this.info = info;
    },
    displayDeleteModal: function (info) {
      this.showDeleteModal = true;
      this.customDeleteMsg =
        "Are you sure you want to cancel the order '" + info.orderId + "' ?";
    },
  },
  mounted: function () {
    this.$root.$on("closeModalEvent", () => {
      this.showUpdateModal = false;
      this.showViewModal = false;
      this.showDeleteModal = false;
    });
  },
};
</script>

<style lang="scss">
</style>
