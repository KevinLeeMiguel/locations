<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <select v-model="province">
      <option v-for="prov in provinces" :key="prov">{{prov}}</option>
    </select>
    <select v-model="district">
      <option value="default">Choose District</option>
      <option v-for="distr in districts" :key="distr">{{distr}}</option>
    </select>
  </div>
</template>

<script>
import { Provinces, Districts } from "./location";
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  data() {
    return {
      provinces: Provinces(),
      province: Provinces()[0],
      district: 'default'
    };
  },
  computed: {
    districts: function() {
      return Districts(this.province);
    }
  },
  created() {}
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
