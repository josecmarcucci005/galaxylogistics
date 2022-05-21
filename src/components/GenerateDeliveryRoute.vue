<template>
  <div>
    <div class="ui form">
      <div class="inline field">
        <div class="field">
          <div class="ui radio checkbox">
            <input
              type="radio"
              name="search"
              tabindex="0"
              checked="true"
              v-on:click="
                routePerDriver = !routePerDriver;
                routePerArea = !routePerArea;
              "
            />
            <label>Route per Delivery Area</label>
          </div>
          <select value="North West" v-bind:disabled="routePerDriver">
            <option disabled value="">Please select one</option>
            <option>North West</option>
            <option>Nort East</option>
            <option>Center</option>
            <option>South West</option>
            <option>South East</option>
          </select>
        </div>
        <br />
        <div class="field">
          <div class="ui radio checkbox">
            <input
              type="radio"
              name="search"
              tabindex="0"
              v-on:click="
                routePerDriver = !routePerDriver;
                routePerArea = !routePerArea;
              "
            />
            <label>Route per Driver</label>
          </div>
          <select value="Marlon Brandon" v-bind:disabled="routePerArea">
            <option disabled value="">Please select one</option>
            <option>Marlon Brandon</option>
            <option>Batman</option>
            <option>Thanos</option>
            <option>Black Panther</option>
          </select>
        </div>
      </div>
    </div>
    <br />
    <div class="ui four column grid">
      <div class="ui four column row">
        <div class="column">
          <iframe
            src="https://www.google.com/maps/embed?pb=London"
            width="500"
            height="450"
            frameborder="0"
            style="border: 0"
            allowfullscreen
          ></iframe>
        </div>
        <div class="column"></div>
        <div class="column"></div>
        <div class="column">
          <div class="ui list">
            <div class="item">
              <img
                class="ui avatar image"
                src="http://semantic-ui.com/images/avatar2/small/rachel.png"
              />
              <div class="content">
                <a class="header">Magic Johnson</a>
                <div class="description">Order #1111</div>
              </div>
            </div>
            <div class="item">
              <img
                class="ui avatar image"
                src="http://semantic-ui.com/images/avatar2/small/lindsay.png"
              />
              <div class="content">
                <a class="header">Denis Rodman</a>
                <div class="description">Order #2222</div>
              </div>
            </div>
            <div class="item">
              <img
                class="ui avatar image"
                src="http://semantic-ui.com/images/avatar2/small/matthew.png"
              />
              <div class="content">
                <a class="header">Michael Jordan</a>
                <div class="description">Order #3333</div>
              </div>
            </div>
            <div class="item">
              <img
                class="ui avatar image"
                src="http://semantic-ui.com/images/avatar/small/jenny.jpg"
              />
              <div class="content">
                <a class="header">Luka Doncic</a>
                <div class="description">Order #4444</div>
              </div>
            </div>
            <div class="item">
              <img
                class="ui avatar image"
                src="http://semantic-ui.com/images/avatar/small/veronika.jpg"
              />
              <div class="content">
                <a class="header">Lebron James</a>
                <div class="description">Order #5555</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "manage-area",
  data() {
    return {
      routePerDriver: false,
      routePerArea: true,
    };
  },
  components: {},
  methods: {},
  mounted: function () {},
};
</script>

<style lang="scss">
</style>
