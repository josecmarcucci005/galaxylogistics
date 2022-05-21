<template>
  <div>
    <div class="ui icon input">
      <input type="text" placeholder="Search Driver..." />
      <i class="search link icon"></i>
    </div>
    <table slot="content" class="ui celled striped table">
      <thead>
        <tr>
          <th>Driver</th>
          <th>Delivery Areas</th>
          <th class="left aligned four wide">Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="content in tableContent" :key="content.id">
          <td>{{ content.driver }}</td>
          <td>
            <div class="ui list" v-for="item in content.areas" :key="item.id">
              <div class="item">{{ item.area }}</div>
            </div>
          </td>
          <td>
            <button
              class="ui small yellow button"
              v-on:click="displayUpdateModal(content)"
            >
              Edit
            </button>
          </td>
        </tr>
      </tbody>
    </table>
    <ModalDriverArea
      v-if="showUpdateModal"
      v-bind="{ info: info, modalType: 'EDIT' }"
    ></ModalDriverArea>
  </div>
</template>

<script>
import ModalDriverArea from "./ModalDriverArea.vue";

export default {
  name: "manage-driver-area",
  data() {
    return {
      tableContent: [
        {
          driver: "Batman",
          areas: [
            {
              area: "North West",
              postCode: "XXXYYY",
              city: "London",
              country: "United Kindom",
            },
            {
              area: "North East",
              postCode: "XXXWWW",
              city: "London",
              country: "United Kindom",
            },
          ],
        },
        {
          driver: "Deadpool",
          areas: [
            {
              area: "South West",
              postCode: "TTTEEE",
              city: "London",
              country: "United Kindom",
            },
            {
              area: "South East",
              postCode: "TTTKKK",
              city: "London",
              country: "United Kindom",
            },
          ],
        }
      ],
      showUpdateModal: false,
      info: {}
    };
  },
  components: {
    ModalDriverArea
  },
  methods: {
    displayUpdateModal: function (info) {
      this.showUpdateModal = true;
      this.info = info;
    }
  },
  mounted: function () {
    this.$root.$on("closeModalEvent", () => {
      this.showUpdateModal = false;
    });
  },
};
</script>

<style lang="scss">
</style>
