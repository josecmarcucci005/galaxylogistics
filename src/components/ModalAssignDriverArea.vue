<template>
  <div class="modal">
    <div class="modal-wrapper">
      <div class="modal-container">
        <content select=".modal-header">
          <div class="modal-header">
            <h3>{{ "ASSIGN AREA" }}</h3>
          </div>
        </content>
        <div class="modal-body">
          <br />
          <div class="ui form">
            <div class="field">
              <label>Driver Name</label>
              <input type="text" v-bind:value="info.driver" />
            </div>
            <br/>
            <div class="field">
              <label>Delivery Area</label>
              <select>
                <option disabled value="">Please select one</option>
                <option>North West</option>
                <option>North East</option>
                <option>Center</option>
                <option>South West</option>
                <option>South East</option>
              </select>
            </div>
          </div>
        </div>
        <div class="modal-footer">
          <button v-on:click="closeModal()">Assign</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "modal-results",
  props: ["info"],
  data() {
    return {
    };
  },
  watch: {
    info: function (info) {
      return info;
    }
  },
  methods: {
    closeModal: function () {
      this.$root.$emit("closeSubModalEvent");
    },
  },
  mounted: function () {},
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
