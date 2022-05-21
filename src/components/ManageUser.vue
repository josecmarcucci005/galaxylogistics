<template>
  <div>
    <button class="ui medium primary button" v-on:click="displayAddModal()">
      <i class="plus icon" />
      Add User
    </button>
    <br/><br/>
    <div class="ui icon input">
      <input type="text" placeholder="Search User..." />
      <i class="search link icon"></i>
    </div>
    <table slot="content" class="ui celled striped table">
      <thead>
        <tr>
          <th>User</th>
          <th>Role</th>
          <th class="left aligned four wide">Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="content in tableContent" :key="content.id">
          <td>{{ content.user }}</td>
          <td>{{ content.role }}</td>
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
    <ModalUser
      v-if="showUpdateModal"
      v-bind="{ userInfo: userInfo, modalType: 'EDIT' }"
    ></ModalUser>
    <ModalUser
      v-if="showAddModal"
      v-bind="{ userInfo: userInfo, modalType: 'ADD' }"
    ></ModalUser>
    <ModalDelete
      v-if="showDeleteModal"
      v-bind="{ customDeleteMsg: customDeleteMsg }"
    ></ModalDelete>

  </div>
</template>

<script>
import ModalUser from "./ModalUser.vue";
import ModalDelete from "./ModalDelete.vue";

export default {
  name: "manage-roles",
  data() {
    return {
      tableContent: [
        { user: "Tom Cruise", role: "Admin" },
        { user: "Tim Werner", role: "Manager" },
        { user: "Luka Modric", role: "Supplier" },
        { user: "Karim Benzema", role: "Driver" },
        { user: "Federico Chiesa", role: "Customer" },
      ],
      showUpdateModal: false,
      showAddModal: false,
      showDeleteModal: false,
      userInfo: {},
      customDeleteMsg : ""
    };
  },
  components: {
    ModalUser,
    ModalDelete
  },
  methods: {
    displayUpdateModal: function (userInfo) {
      this.showUpdateModal = true;
      this.userInfo = userInfo;
    },
    displayAddModal: function () {
      this.showAddModal = true;
      this.userInfo = {};
    },
    displayDeleteModal: function (userInfo) {
      this.showDeleteModal = true;
      this.customDeleteMsg = "Are you sure you want to delete the user '" + userInfo.user + "' ?" ;
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
