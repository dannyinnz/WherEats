<template>
  <div class="vote">
    <h1>{{ msg }}</h1>
    <p>Please vote for the cafeteria to eat today!</p>
    <a
      href="https://fphcareonline.sharepoint.com/sites/Facilities/SitePages/Cafeteria.aspx?web=1"
      target="_blank"
      rel="noopener"
    >This week's menu</a>
    <p />
    <div id="example-1">
      <v-if></v-if>
      <button
        v-bind:class="{ selectedButton: (lastClicked == 1) }"
        v-on:click="
        defaultColors = [ '#9EDE00', '#e7e7e7', '#e7e7e7', '#e7e7e7' ];
        lastClicked = 1;
        counterStewart += 1;
        scrollToGraph();
        "
      >Stewart</button>
      <button
        v-bind:class="{ selectedButton: (lastClicked == 2) }"
        v-on:click="
        defaultColors = [ '#e7e7e7', '#9EDE00', '#e7e7e7', '#e7e7e7' ];
        lastClicked = 2;
        counterOhare += 1;
        scrollToGraph();
        "
      >Ohare</button>
    </div>
    <div>
      <button
        v-bind:class="{ selectedButton: (lastClicked == 3) }"
        v-on:click="
        defaultColors = [ '#e7e7e7', '#e7e7e7', '#9EDE00', '#e7e7e7' ];
        lastClicked = 3;
        counterPaykel += 1;
        scrollToGraph();
        "
      >Paykel</button>
      <button
        v-bind:class="{ selectedButton: (lastClicked == 4) }"
        v-on:click="
        defaultColors = [ '#e7e7e7', '#e7e7e7', '#e7e7e7', '#9EDE00' ];
        lastClicked = 4;
        counterHub += 1;
        scrollToGraph();
        "
      >The Hub</button>
    </div>

    <div id="graph">
      <h2>Top Voted Cafe: 21/01/2020</h2>
      <graph-bar
        :width="600"
        :height="400"
        :axis-min="0"
        :axis-max="10"
        :labels="[ '' ]"
        :colors="defaultColors"
        :values="[[counterStewart],[counterOhare],[counterPaykel],[counterHub]]"
      >
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
      lastClicked: 0,
      defaultColors: ["#e7e7e7", "#e7e7e7", "#e7e7e7", "#e7e7e7"],
      names: ["Stewart", "O'Hare", "Paykel", "Hub"]
    };
  },
  methods: {
    scrollToGraph: function() {
      var elmnt = document.getElementById("graph");
      elmnt.scrollIntoView();
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
button {
  height: 150px;
  width: 150px;
  margin: 10px;
  font-size: 20px;
}
.selectedButton {
  background-color: #9ede00;
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
