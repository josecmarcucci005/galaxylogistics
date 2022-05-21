<template>
  <div class="modal">
    <div class="modal-wrapper">
      <div class="modal-container">
        <content select=".modal-header">
          <div class="modal-header">
            <h3>Edit Role</h3>
          </div>
        </content>
        <div class="modal-body">
          <br />
          <div class="ui form">
            <div class="field">
              <label>Role Name</label>
              <input type="text" v-bind:value="roleInfo.role" />
            </div>
            <div class="field">
              <label>Description</label>
              <input type="text" v-bind:value="roleInfo.description" />
            </div>
          </div>
          <div class="ui secondary segment">
            <p style="font-size: 15px"><b>Rights</b></p>
          </div>
          <div class="ui four column grid">
            <div class="three column row">
              <div class="column">
                <div class="ui list">
                  <div class="item">
                    <div class="content">
                      <div class="ui blue header">Roles Options</div>
                      <div class="ui checkbox">
                        <input type="checkbox" checked="true" />
                        <label>Edit Role</label>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <div class="column">
                <div class="ui list">
                  <div class="item">
                    <div class="content">
                      <div class="ui blue header">Product Options</div>
                      <div class="ui checkbox">
                        <input type="checkbox" checked="true" />
                        <label>Create Product</label>
                      </div>
                      <div class="ui checkbox">
                        <input type="checkbox" checked="true" />
                        <label>Edit Product</label>
                      </div>
                      <div class="ui checkbox">
                        <input type="checkbox" checked="true" />
                        <label>Delete Product</label>
                      </div>
                      <div class="ui checkbox">
                        <input type="checkbox" />
                        <label>Update Inventory</label>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <div class="column">
                <div class="ui list">
                  <div class="item">
                    <div class="content">
                      <div class="ui blue header">Delivery Options</div>
                      <div class="ui checkbox">
                        <input type="checkbox" checked="true" />
                        <label>Create Delivery Area</label>
                      </div>
                      <div class="ui checkbox">
                        <input type="checkbox" checked="true" />
                        <label>Edit Delivery Area</label>
                      </div>
                      <div class="ui checkbox">
                        <input type="checkbox" checked="true" />
                        <label>Delete Delivery Area</label>
                      </div>
                      <div class="ui checkbox">
                        <input type="checkbox" checked="true"/>
                        <label>Assign Delivery Area to Driver</label>
                      </div>
                      <div class="ui checkbox">
                        <input type="checkbox" checked="true"/>
                        <label>Generate Delivery Route</label>
                      </div>
                    </div>
                  </div>
                </div>
              </div>    
            </div>
            <div class="three column row">
              <div class="column">
                <div class="ui list">
                  <div class="item">
                    <div class="content">
                      <div class="ui blue header">Users Options</div>
                      <div class="ui checkbox">
                        <input type="checkbox" checked="true" />
                        <label>Crate User</label>
                      </div>
                      <br/>
                      <div class="ui checkbox">
                        <input type="checkbox" checked="true" />
                        <label>Edit User</label>
                      </div>
                      <br/>
                      <div class="ui checkbox">
                        <input type="checkbox" checked="true" />
                        <label>Delete User</label>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <div class="column">
                <div class="ui list">
                  <div class="item">
                    <div class="content">
                      <div class="ui blue header">Order Options</div>
                      <div class="ui checkbox">
                        <input type="checkbox" />
                        <label>Create Order</label>
                      </div>
                      <div class="ui checkbox">
                        <input type="checkbox" checked="true" />
                        <label>View Orders</label>
                      </div>
                      <div class="ui checkbox">
                        <input type="checkbox" checked="true" />
                        <label>Update Orders</label>
                      </div>
                      <div class="ui checkbox">
                        <input type="checkbox" checked="true"/>
                        <label>Cancel Orders</label>
                      </div>
                      <div class="ui checkbox">
                        <input type="checkbox" />
                        <label>Pay Orders</label>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <div class="column">
                <div class="ui list">
                  <div class="item">
                    <div class="content">
                      <div class="ui blue header">Category Options</div>
                      <div class="ui checkbox">
                        <input type="checkbox" checked="true" />
                        <label>Create Category</label>
                      </div>
                      <div class="ui checkbox">
                        <input type="checkbox" checked="true" />
                        <label>Edit Category</label>
                      </div>
                      <div class="ui checkbox">
                        <input type="checkbox" checked="true" />
                        <label>Delete Category</label>
                      </div>
                    </div>
                  </div>
                </div>
              </div>    
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
  props: ["roleInfo"],
  data() {
    return {};
  },
  watch: {
    roleInfo: function (roleInfo) {
      return roleInfo;
    },
  },
  methods: {
    closeModal: function () {
      this.$root.$emit("closeEditModalEvent");
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
