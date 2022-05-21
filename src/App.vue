<template>
  <div class="ui container">
    <logistics></logistics>
  </div>
</template>

<script>
import Logistics from "./components/Logistics.vue";
import { loadScript } from "vue-plugin-load-script";

export default {
  name: "app",
  data() {
    return {
    };
  },
  components: {
    Logistics
  },
  mounted: function () {
    loadScript(
      "//cdnjs.cloudflare.com/ajax/libs/semantic-ui/2.0.7/semantic.min.js"
    );
    loadScript("//cdn.quilljs.com/0.16.0/quill.min.js");
    loadScript(
      "//cdnjs.cloudflare.com/ajax/libs/vue-resource/1.5.1/vue-resource.min.js"
    );
    loadScript("//cdnjs.cloudflare.com/ajax/libs/vue/2.6.11/vue.min.js");
    loadScript("//cdnjs.cloudflare.com/ajax/libs/axios/0.15.3/axios.min.js");
    loadScript("//ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js");
    loadScript("//tyleryasaka.github.io/semantic-ui-range/range.js");
    loadScript("//unpkg.com/vuetify@0.16.9/dist/vuetify.min.js");
  },
};
</script>

<style>
@import "//cdnjs.cloudflare.com/ajax/libs/semantic-ui/2.0.7/semantic.min.css";
@import "//cdn.quilljs.com/0.16.0/quill.snow.css";
@import "//cdnjs.cloudflare.com/ajax/libs/uikit/2.22.0/css/uikit.almost-flat.min.css";
</style>
