<template>
  <div class="modal">
    <div class="modal-wrapper">
      <div class="modal-container">
        <content select=".modal-header">
          <div class="modal-header">
            <h3>{{modalType == 'EDIT' ? 'EDIT DELIVERY AREA' : 'ADD DELIVERY AREA'}}</h3>
          </div>
        </content>
        <div class="modal-body">
          <br />
          <div class="ui form">
            <div class="field">
              <label>Area Name</label>
              <input type="text" v-bind:value="info.area"/>
            </div>
            <div class="field">
              <label>Post Code</label>
              <select v-bind:value="info.postCode">
                <option disabled value="">Please select one</option>
                <option>XXXYYY</option>
                <option>XXXWWW</option>
                <option>VVVAAA</option>
                <option>TTTEEE</option>
                <option>TTTKKK</option>
                <option>WWWWWW</option>
              </select>
            </div>
            <div class="field">
              <label>City</label>
              <select v-bind:value="info.city">
                <option disabled value="">Please select one</option>
                <option>London</option>
                <option>Liverpool</option>
                <option>Manchester</option>
              </select>
            </div>
            <div class="field">
              <label>Country</label>
              <select v-bind:value="info.country">
                <option disabled value="">Please select one</option>
                <option>United Kindom</option>
                <option>Spain</option>
                <option>Czech Republic</option>
              </select>
            </div>
          </div>
        </div>  
        <div class="modal-footer">
          <button v-on:click="closeModal()">Ok</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "modal-results",
  props: ["info", "modalType"],
  data() {
    return {
      user : {}
    };
  },
  watch: {
    info: function (info) {
      return info;
    },
    modalType: function(modalType) {
      return modalType;
    }
  },
  methods: {
    closeModal: function () {
      this.$root.$emit("closeModalEvent");
    },
  },
  mounted: function () {
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
