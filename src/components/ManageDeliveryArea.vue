<template>
  <div>
    <button class="ui medium primary button" v-on:click="displayAddModal()">
      <i class="plus icon" />
      Add Area
    </button>
    <br/><br/>
    <div class="ui icon input">
      <input type="text" placeholder="Search Delivery Area..." />
      <i class="search link icon"></i>
    </div>
    <table slot="content" class="ui celled striped table">
      <thead>
        <tr>
          <th>Area</th>
          <th>Post Code</th>
          <th>City</th>
          <th>Country</th>
          <th class="left aligned four wide">Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="content in tableContent" :key="content.id">
          <td>{{ content.area }}</td>
          <td>{{ content.postCode }}</td>
          <td>{{ content.city }}</td>
          <td>{{ content.country }}</td>
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
    <ModalDeliveryArea
      v-if="showUpdateModal"
      v-bind="{ info: info, modalType: 'EDIT' }"
    ></ModalDeliveryArea>
    <ModalDeliveryArea
      v-if="showAddModal"
      v-bind="{ info: info, modalType: 'ADD' }"
    ></ModalDeliveryArea>
    <ModalDelete
      v-if="showDeleteModal"
      v-bind="{ customDeleteMsg: customDeleteMsg }"
    ></ModalDelete>

  </div>
</template>

<script>
import ModalDeliveryArea from "./ModalDeliveryArea.vue";
import ModalDelete from "./ModalDelete.vue";

export default {
  name: "manage-area",
  data() {
    return {
      tableContent: [
        { area: "North West", postCode: "XXXYYY", city: "London", country : "United Kindom" },
        { area: "North East", postCode: "XXXWWW", city: "London", country : "United Kindom" },
        { area: "Center", postCode: "VVVAAA", city: "London", country : "United Kindom" },
        { area: "South West", postCode: "TTTEEE", city: "London", country : "United Kindom" },
        { area: "South East", postCode: "TTTKKK", city: "London", country : "United Kindom" },
      ],
      showUpdateModal: false,
      showAddModal: false,
      showDeleteModal: false,
      info: {},
      customDeleteMsg : ""
    };
  },
  components: {
    ModalDeliveryArea,
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
      this.customDeleteMsg = "Are you sure you want to delete the area '" + info.area + "' ?" ;
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
