<template>
  <div class="modal">
    <div class="modal-wrapper">
      <div class="modal-container">
        <content select=".modal-header">
          <div class="modal-header">
            <h3>{{ "EDIT DRIVER AREA" }}</h3>
          </div>
        </content>
        <div class="modal-body">
          <br/>
          <button
            class="ui medium primary button"
            v-on:click="displayAddModal()"
          >
            <i class="plus icon" />
            Assign Area
          </button>
          <br />
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
              <tr v-for="content in info.areas" :key="content.id">
                <td>{{ content.area }}</td>
                <td>{{ content.postCode }}</td>
                <td>{{ content.city }}</td>
                <td>{{ content.country }}</td>
                <td>
                  <button
                    class="ui small red button"
                    v-on:click="displayDeleteModal(content)"
                  >
                    Unassingn
                  </button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
        <div class="modal-footer">
          <button v-on:click="closeModal()">Ok</button>
        </div>
      </div>
    </div>
    <ModalAssignDriverArea
      v-if="showAddModal"
      v-bind="{ info: info }"
    ></ModalAssignDriverArea>
    <ModalDelete
      v-if="showDeleteModal"
      v-bind="{ customDeleteMsg: customDeleteMsg }"
    ></ModalDelete>
  </div>
</template>

<script>
import ModalAssignDriverArea from "./ModalAssignDriverArea.vue";
import ModalDelete from "./ModalDelete.vue";

export default {
  name: "modal-results",
  props: ["info", "modalType"],
  data() {
    return {
      showAddModal: false,
      showDeleteModal: false,
      customDeleteMsg : ""
    };
  },
  components: {
    ModalAssignDriverArea,
    ModalDelete
  },
  watch: {
    info: function (info) {
      return info;
    },
    modalType: function (modalType) {
      return modalType;
    },
  },
  methods: {
    closeModal: function () {
      this.$root.$emit("closeModalEvent");
    },
    displayAddModal: function () {
      this.showAddModal = true;
    },
    displayDeleteModal: function (info) {
      this.showDeleteModal = true;
      this.customDeleteMsg = "Are you sure you want to unassign the area '" + info.area + "' ?" ;
    }
  },
  mounted: function () {
    this.$root.$on("closeSubModalEvent", () => {
      this.showAddModal = false;
    });
  },
};
</script>

<style lang="scss">
.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.7);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  background: #fff;
  width: 650px;
  border-radius: 5px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
  margin: 0 auto;
  padding: 20px 30px;
}

.modal-footer {
  margin-top: 15px;
}

.modal-enter,
.modal-leave {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave .modal-container {
  -webkit-transform: scale(1.1);
  transform: scale(1.1);
}
</style>
