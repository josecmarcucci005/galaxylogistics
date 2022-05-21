<template>
  <div>
  <table slot="content" class="ui celled striped table">
    <caption class="ui blue inverted segment">
      <p style="font-size: 20px">Roles</p>
    </caption>
    <thead>
      <tr>
        <th>Name</th>
        <th>Description</th>
        <th>Rights</th>
        <th>Actions</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(content, index) in tableContent" :key="content.id">
        <td>{{ content.role }}</td>
        <td>{{ content.description }}</td>
        <td>
          <div class="ui tiny list" v-for="right in tableContent[index].rights" :key="right.id">
            <div class="item">{{ right }}</div>
          </div>
        </td>
        <td>
          <button class="ui small primary button" v-on:click="displayModal(content)">Edit
          </button >
        </td>  
      </tr>
    </tbody>
  </table>
  <ModalEditRole v-if="showModal" v-bind="{ 'roleInfo': roleInfo }"></ModalEditRole>
  </div>
</template>

<script>
import ModalEditRole from './ModalEditRole.vue';

export default {
  name: "manage-roles",
  data() {
    return {
      tableContent : [
        { role: 'Admin', description: 'This is the admin role', rights: ['Edit Roles', 'Manage Users', 'Manage Products', 'Manage Orders', 'Manage Delivery'] },
        { role: 'Manager', description: 'This is the manager role', rights: ['Manage Products', 'Manage Orders', 'Manage Delivery'] },
        { role: 'Supplier', description: 'This is the supplier role', rights: ['Manage Products', 'Manage Orders'] },
        { role: 'Customer', description: 'This is the customer role', rights: ['Create/Edit Orders'] },
        { role: 'Driver', description: 'This is the driver role', rights: ['Assign Delivery Area', 'Generate Delivery Route', 'Update Orders'] }
      ],
      showModal : false,
      roleInfo : {}
    };
  },
  components : {
    ModalEditRole
  },
  methods: {
    displayModal: function(roleInfo) {
      this.showModal = true;
      this.roleInfo = roleInfo;
    }
  },
  mounted: function () {
    this.$root.$on('closeEditModalEvent', () => {
      this.showModal = false;
    })
  },
};
</script>

<style lang="scss">
</style>
