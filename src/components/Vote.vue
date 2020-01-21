<template>
  <div class="vote">
    <h1>{{ msg }}</h1>
    <p>Please vote for the cafeteria to eat today!</p>
    <a href="https://fphcareonline.sharepoint.com/sites/Facilities/SitePages/Cafeteria.aspx?web=1" target="_blank" rel="noopener">This week's menu</a>
    <p/>
    <div id="example-1">
      <button style="background-color: #4CAF50" v-on:click="counterStewart += 1">Stewart</button>
      <button style="background-color: #4CAF50" v-on:click="counterOhare += 1">Ohare</button>
    </div>
    <div>
      <button style="background-color: #4CAF50" v-on:click="counterPaykel += 1">Paykel</button>
      <button style="background-color: #4CAF50" v-on:click="counterHub += 1">The Hub</button>
    </div>
    <h1>{{counter}}</h1>
    <div id="app">
      <graph-bar
        :width="600"
        :height="400"
        :axis-min="0"
        :axis-max="10"
        :labels="[ '' ]"
        :values="[[counterStewart],[counterOhare],[counterPaykel],[counterHub]]"
      >
        <note :text="'Top Voted Cafe: 21/01/2020'"></note>
        <tooltip :names="names" :position="'left'"></tooltip>
        <legends :names="names"></legends>
      </graph-bar>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import GraphLine3D from "vue-graph/src/components/line3d.js";
import NoteWidget from "vue-graph/src/widgets/note.js";
import LegendWidget from "vue-graph/src/widgets/legends.js";

Vue.component(GraphLine3D.name, GraphLine3D);
Vue.component(NoteWidget.name, NoteWidget);
Vue.component(LegendWidget.name, LegendWidget);

export default {
  name: "Vote",
  props: {
    msg: String
  },
  data: function() {
    return {
      counterStewart: 0,
      counterOhare: 0,
      counterPaykel: 0,
      counterHub: 0,
      names: ["Stewart", "O'Hare", "Paykel", "Hub"]
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
button {
  height: 150px;
  width: 150px;
  margin: 10px;
}
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
