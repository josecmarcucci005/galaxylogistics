<template>
  <div class="modal">
    <div class="modal-wrapper">
      <div class="modal-container">
        <content select=".modal-header">
          <div class="modal-header">
            <h3>DELETE CONFIRMATION</h3>
          </div>
        </content>
        <br/>
        <div class="modal-body">
          <div class="ui negative message">
             {{customDeleteMsg}}
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
  props: ["customDeleteMsg"],
  data() {
    return {
      user : {}
    };
  },
  watch: {
    customDeleteMsg: function (customDeleteMsg) {
      return customDeleteMsg;
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
