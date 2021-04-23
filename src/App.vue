<template>
	<div id="title">
    <Develop v-show="developement" />
		<h1>Hello, world</h1>
    <CheckButton text="Message" v-model="checkValue" hue="30" darkmode />
	</div>
</template>

<script>
import Develop from "./components/Develop.vue";
import CheckButton from './components/CheckButton.vue';

export default {
  name: "App",
  components: {
    Develop,
    CheckButton,
  },
  data: function() {
    return {
      view: "top",
      articlePath: "",
      isColorEdit: false,
      scrollParam: {},
      checkValue: false,
    };
  },
  watch: {
    checkValue(newv, oldv) {
      console.log(`${oldv} -> ${newv}`);
    },
  },
  computed: {
    developement: () => process.env.NODE_ENV && process.env.NODE_ENV.startsWith('development'),
  },
  methods: {
    windowLoad: function() {
//      this.scrollParam.target = document.querySelector("#navi");
    },
  },
  mounted: function() {
    window.addEventListener("load", this.windowLoad, {
      once: true,
      passive: true
    });
    dispatchEvent(new PopStateEvent("popstate", {}));
  },
  destroyed: function() {
    window.removeEventListener("load", this.windowLoad, {
      once: true,
      passive: true
    });
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
html {
 overflow-y: scroll;
}
::-webkit-scrollbar {
  width: 12px;
}
::-webkit-scrollbar-track {
  background: #ccc;
}
::-webkit-scrollbar-thumb {
  background: #333;
  border-radius: 6px;
}
body {
  margin: 0;
}

@media screen and (max-width: 400px) {
  #logo {
    width: 240px;
    height: 240px;
  }
  #title_message {
    writing-mode: vertical-lr;
    margin: 1em 0;
  }
  #title_info label,
  #title_info button {
    display: none;
  }
}
@media screen and (max-width: 300px) {
  #logo {
    width: 180px;
    height: 180px;
  }
  #title_message {
    writing-mode: vertical-lr;
    margin: 1em 0;
  }
  #title_info label,
  #title_info button {
    display: none;
  }
}
</style>