<template>
  <div>
    <call-player :called="called" @call="handler"/>
    <user-lists :userlists="userlists"/>
  </div>
</template>

<script>
import CallPlayer from "./components/CallPlayer.vue";
import UserLists from "./components/UserLists.vue";

export default {
  name: "App",
  components: {
    CallPlayer,
    UserLists
  },
  data() {
    return {
      called: "",
      userlists: [
        {
          id: 0,
          name: "こさく",
          max: 100,
          current: 100
        },
        {
          id: 2,
          name: "まさし",
          max: 200,
          current: 200
        },
        {
          id: 3,
          name: "のん",
          max: 70,
          current: 70
        }
      ],
      called: 0
    };
  },
  methods: {
    handler: function(index) {
      this.userlists[index].current -= 10
    }
  }
};
</script>


