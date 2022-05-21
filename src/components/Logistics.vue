<template>
  <div class="ui container">
    <br />
    <div class="ui blue inverted segment">
      <div class="ui blue inverted menu">
        <div class="left item">
          <h1 class="ui inverted header">GALAXYLOGISTICS</h1>
        </div>
        <div class="center item">
          <div class="ui icon input">
            <input type="text" placeholder="Search..." />
            <i class="search link icon"></i>
          </div>
        </div>
        <div class="right item">
          <img
            class="ui tiny right spaced top aligned circular image"
            src="http://semantic-ui.com/images/avatar2/large/patrick.png"
          />
          <div>
            Welcome to <b>GalaxyLogistics!</b>
            <p style="font-size: 20px">Jose Marcucci</p>
            Your last login: 10.05.2022 10:30:00
            <p></p>
            <div class="ui tiny red label">22</div>
            <i aria-hidden="true" class="mail icon"></i>
            Messages
          </div>
        </div>
      </div>
    </div>
    <div class="ui divider"></div>
    <div class="ui grid">
      <div class="three wide column">
        <div class="ui vertical pointing menu">
          <a v-bind:class="menuSelect[0].class" v-on:click.prevent="menuSelect[0].activeMenu = true; menuSelect[0].class = 'active blue item';
          menuSelect[1].activeMenu = false; menuSelect[1].class = 'item'
          menuSelect[2].activeMenu = false; menuSelect[2].class = 'item'
          menuSelect[3].activeMenu = false; menuSelect[3].class = 'item'">
            <i class="left icon user"></i>
            <div style="font-size: medium">Users</div>
          </a>
          <div class="item" v-if="menuSelect[0].activeMenu">
            <div class="menu">
              <a v-bind:class="menuSelect[0].submenu[0].class" v-on:click.prevent="menuSelect[0].submenu[0].class = 'active item'; menuSelect[0].submenu[1].class = 'item'; 
              menuSelect[0].submenu[0].active = true; menuSelect[0].submenu[1].active = false;">Manage Roles</a>
              <a v-bind:class="menuSelect[0].submenu[1].class" v-on:click.prevent="menuSelect[0].submenu[0].class = 'item'; menuSelect[0].submenu[1].class = 'active item'; 
              menuSelect[0].submenu[0].active = false; menuSelect[0].submenu[1].active = true;">Manage Users</a>
            </div>
          </div>
          <a v-bind:class="menuSelect[1].class" v-on:click.prevent="menuSelect[0].activeMenu = false; menuSelect[0].class = 'item';
          menuSelect[1].activeMenu = true; menuSelect[1].class = 'active blue item';
          menuSelect[2].activeMenu = false; menuSelect[2].class = 'item';
          menuSelect[3].activeMenu = false; menuSelect[3].class = 'item';">
            <i class="left cube icon"></i>
            <div style="font-size: medium">Products</div>
          </a>
          <div class="item" v-if="menuSelect[1].activeMenu">
            <div class="menu">
              <a v-bind:class="menuSelect[1].submenu[0].class" v-on:click.prevent="menuSelect[1].submenu[0].class = 'active item'; menuSelect[1].submenu[1].class = 'item'; 
              changeSubMenuProduct();">Manage Categories</a>
              <a v-bind:class="menuSelect[1].submenu[1].class" v-on:click.prevent="menuSelect[1].submenu[0].class = 'item'; menuSelect[1].submenu[1].class = 'active item'; 
              changeSubMenuProduct();">Manage Products</a>
            </div>
          </div>  
          <a v-bind:class="menuSelect[2].class" v-on:click.prevent="menuSelect[0].activeMenu = false; menuSelect[0].class = 'item';
          menuSelect[1].activeMenu = false; menuSelect[1].class = 'item';
          menuSelect[2].activeMenu = true; menuSelect[2].class = 'active blue item';
          menuSelect[3].activeMenu = false; menuSelect[3].class = 'item';">
            <i class="left shopping cart icon"></i>
            <div style="font-size: medium">Orders</div>
          </a>
          <div class="item" v-if="menuSelect[2].activeMenu">
            <div class="menu">
              <a class="active item">Manage Orders</a>
            </div>
          </div>  
          <a v-bind:class="menuSelect[3].class" v-on:click.prevent="menuSelect[0].activeMenu = false; menuSelect[0].class = 'item';
          menuSelect[1].activeMenu = false; menuSelect[1].class = 'item';
          menuSelect[2].activeMenu = false; menuSelect[2].class = 'item';
          menuSelect[3].activeMenu = true; menuSelect[3].class = 'active blue item';">
            <i class="left truck icon"></i>
            <div style="font-size: medium">Delivery</div>
          </a>
          <div class="item" v-if="menuSelect[3].activeMenu">
            <div class="menu">
              <a v-bind:class="menuSelect[3].submenu[0].class" v-on:click.prevent="menuSelect[3].submenu[0].class = 'active item'; menuSelect[3].submenu[1].class = 'item'; menuSelect[3].submenu[2].class = 'item'; 
              menuSelect[3].submenu[0].active = true; menuSelect[3].submenu[1].active = false; menuSelect[3].submenu[2].active = false;">Manage Delivery Areas</a>
              <a v-bind:class="menuSelect[3].submenu[1].class" v-on:click.prevent="menuSelect[3].submenu[0].class = 'item'; menuSelect[3].submenu[1].class = 'active item'; menuSelect[3].submenu[2].class = 'item'; 
              menuSelect[3].submenu[0].active = false; menuSelect[3].submenu[1].active = true; menuSelect[3].submenu[2].active = false;">Generate Delivery Route</a>
              <a v-bind:class="menuSelect[3].submenu[2].class" v-on:click.prevent="menuSelect[3].submenu[0].class = 'item'; menuSelect[3].submenu[1].class = 'item'; menuSelect[3].submenu[2].class = 'active item'; 
              menuSelect[3].submenu[0].active = false; menuSelect[3].submenu[1].active = false; menuSelect[3].submenu[2].active = true;">Manage Drivers Area</a>
            </div>
          </div>  
        </div>
      </div>
      <div class="one wide column"></div>
      <div class="ten wide column">
        <ManageRole v-if="menuSelect[0].activeMenu == true && menuSelect[0].submenu[0].active == true"/>
        <ManageUser v-if="menuSelect[0].activeMenu == true && menuSelect[0].submenu[1].active == true"/>
        <ManageCategory v-if="menuSelect[1].activeMenu == true && menuSelect[1].submenu[0].active == true"/>
        <ManageProduct v-if="menuSelect[1].activeMenu == true && menuSelect[1].submenu[1].active == true"/>
        <ManageOrders v-if="menuSelect[2].activeMenu == true"/>
        <ManageDeliveryArea v-if="menuSelect[3].activeMenu == true && menuSelect[3].submenu[0].active == true"/>
        <GenerateDeliveryRoute v-if="menuSelect[3].activeMenu == true && menuSelect[3].submenu[1].active == true"/>
        <ManageDriverArea v-if="menuSelect[3].activeMenu == true && menuSelect[3].submenu[2].active == true"/>
      </div>
    </div>
  </div>
</template>


<script>
import "regenerator-runtime";
import ManageRole from './ManageRole.vue';
import ManageUser from './ManageUser.vue';
import ManageCategory from './ManageCategory.vue';
import ManageProduct from './ManageProduct.vue';
import ManageOrders from './ManageOrders.vue';
import ManageDeliveryArea from './ManageDeliveryArea.vue';
import GenerateDeliveryRoute from './GenerateDeliveryRoute.vue';
import ManageDriverArea from './ManageDriverArea.vue';

export default {
  name: "galaxy-logistics",
  data() {
    return {
      menuSelect : [
        { activeMenu: true, class: 'active blue item', submenu: [{active: true, class: 'active item' }, {active: false, class: 'item' }] },
        { activeMenu: false, class: 'item', submenu: [{active: true, class: 'active item' }, {active: false, class: 'item' }] },
        { activeMenu: false, class: 'item', submenu: [{active: true, class: 'active item' }] },
        { activeMenu: false, class: 'item', submenu: [{active: true, class: 'active item' }, {active: false, class: 'item' }, {active: false, class: 'item' }] },
      ]
    };
  },
  components : {
    ManageRole,
    ManageUser,
    ManageCategory,
    ManageProduct,
    ManageOrders,
    ManageDeliveryArea,
    GenerateDeliveryRoute,
    ManageDriverArea
  },
  methods: {
    changeSubMenuProduct : function() {
      this.menuSelect[1].submenu[0].active = !this.menuSelect[1].submenu[0].active; 
      this.menuSelect[1].submenu[1].active = !this.menuSelect[1].submenu[1].active;
    }
  },
};
</script>

<style lang="scss">
.quarter {
  position: absolute;
  width: 50%;
  height: 50%;
  transition: background-color 0.2s ease-in-out;
  cursor: pointer;
}

.quarter1 {
  top: 0;
  left: 0;
  --background: red;
  background: radial-gradient(circle at 100px 100px, red, #610202);
  border: 0.1rem solid #222222;
  border-radius: 100% 0 0 0;
  opacity: 0.4;
}

.quarter2 {
  top: 0;
  right: 0;
  --background-color: blue;
  background: radial-gradient(circle at 100px 100px, #20defc, #020995);
  border-radius: 0 100% 0 0;
  border: 0.1rem solid #222222;
  opacity: 0.4;
}

.quarter3 {
  bottom: 0;
  left: 0;
  --background-color: yellow;
  background: radial-gradient(circle at 100px 100px, yellow, #777703);
  border-radius: 0 0 0 100%;
  border: 0.1rem solid #222222;
  opacity: 0.4;
}

.quarter4 {
  bottom: 0;
  right: 0;
  --background-color: lime;
  background: radial-gradient(circle at 100px 100px, lime, #0f5501);
  border-radius: 0 0 100% 0;
  border: 0.1rem solid #222222;
  opacity: 0.4;
}

.cutout {
  width: 25%;
  height: 25%;
  background-color: #333333;
  background: radial-gradient(circle at 30px 100px, #555555, black);
  position: absolute;
  top: 37%;
  left: 37%;
  border-radius: 50%;
  pointer-events: none;
  text-align: center;
  color: white;
}

.fullcircle {
  position: relative;
  width: 350px;
  height: 350px;
  border-radius: 50%;
  background: #333333;
}

.rangeVeryEasy {
  -webkit-appearance: none;
  border-width: 2px;
  border-style: solid;
  background: #666666;
  border-radius: 50rem;
  border-color: rgba(0, 0, 0, 0.1);
  padding: 3px 5px;
}

.rangeVeryEasy::-webkit-slider-thumb {
  -webkit-appearance: none;
  background: blue;
  border-radius: 50rem;
  height: 0.8em;
  width: 0.8em;
}

.rangeEasy {
  -webkit-appearance: none;
  border-width: 2px;
  border-style: solid;
  background: #666666;
  border-radius: 50rem;
  border-color: rgba(0, 0, 0, 0.1);
  padding: 3px 5px;
}

.rangeEasy::-webkit-slider-thumb {
  -webkit-appearance: none;
  background: #89b84c;
  border-radius: 50rem;
  height: 0.8em;
  width: 0.8em;
}

.rangeMedium {
  -webkit-appearance: none;
  border-width: 2px;
  background: #666666;
  border-style: solid;
  border-radius: 50rem;
  border-color: rgba(0, 0, 0, 0.1);
  padding: 3px 5px;
}

.rangeMedium::-webkit-slider-thumb {
  -webkit-appearance: none;
  background: yellow;
  border-radius: 50rem;
  height: 0.8em;
  width: 0.8em;
}

.rangeHard {
  -webkit-appearance: none;
  border-width: 2px;
  border-style: solid;
  background: #666666;
  border-radius: 50rem;
  border-color: rgba(0, 0, 0, 0.1);
  padding: 3px 5px;
}

.rangeHard::-webkit-slider-thumb {
  -webkit-appearance: none;
  background: orange;
  border-radius: 50rem;
  height: 0.8em;
  width: 0.8em;
}

.rangeVeryHard {
  -webkit-appearance: none;
  border-width: 2px;
  border-style: solid;
  background: #666666;
  border-radius: 50rem;
  border-color: rgba(0, 0, 0, 0.1);
  padding: 3px 5px;
}

.rangeVeryHard::-webkit-slider-thumb {
  -webkit-appearance: none;
  background: red;
  border-radius: 50rem;
  height: 0.8em;
  width: 0.8em;
}
</style>
