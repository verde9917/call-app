<template>
  <div>
    <h3>飲み会参加者</h3>
    <ul>
      <li v-for="user in userlists" v-bind:key="user.id">
        <p>{{ user.name }}</p>
        <span id="hp">{{ user.current }} / {{ user.max }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "UserLists",
  props: {
    "userlists": Array,
    "called": Number,
  },
  data() {
    return {
      users: [
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
        },
      ]
    }
  }
};
</script>
