<template>
  <div>
    <h3>コール再生</h3>​
    <p id="target">乾杯しましょう！</p>
    <audio preload="auto" id="call-player">
      <source src />
    </audio>
    <button type="button" class="btn1" v-on:click="callName">
      指名
    </button>
    <button type="button" class="btn1" v-on:click="startCall">
      コール開始
    </button>
  </div>
</template>

<script>
export default {
  name: "CallPlayer",
  props: ["called"],
  data() {
    return {
      usernum: 0,
      usercount: 3,
      callvars: 10,
      user: [
        {
          id: 0,
          name: "こさく",
          max: 100,
          current: 100
        },
        {
          id: 1,
          name: "まさし",
          max: 200,
          current: 200
        },
        {
          id: 2,
          name: "のん",
          max: 70,
          current: 70
        }
      ]
    };
  },
  methods: {
    callName: function() {
      let rand_player = Math.floor(Math.random() * this.usercount);
      // print + 音声で指名
      const element = document.getElementById("target");
      element.innerText =
        this.user[rand_player].name + "さんが飲んでください。";
      const uttr = new SpeechSynthesisUtterance(
        this.user[rand_player].name + "さんが飲んでください。"
      );
      speechSynthesis.speak(uttr);
      this.usernum = rand_player;
    },
    startCall: function() {
      this.$emit("call", this.usernum);
      let player = document.getElementById("call-player");
      let rand = Math.floor(Math.random() * this.callvars) + 1; //乱数を発生
      let path = "./call/call-" + rand + ".mp3";
      document.querySelector("#call-player source").src = path;
      document.querySelector("#call-player").load();
      player.play();
    }
  }
};
</script>

