<template>
  <form @submit.prevent="onSubmit">
    <textarea v-model="body" required placeholder="Type tweet here"></textarea>
    <br />
    <button class="btn btnTweet" type="submit">Post Tweet</button>
  </form>
</template>

<script>
import { ref } from "vue";
export default {
  emits: ["onSubmit"],
  setup(_, { emit }) {
    const body = ref("");
    const onSubmit = () => {
      emit("onSubmit", {
        id: Math.round(Math.random() * 30),
        avatar: `https://avatars.dicebear.com/api/croodles/${Date.now()}.svg`,
        body: body.value,
        date: new Date(Date.now()).toLocaleString(),
        likes: 0,
      });
      body.value = "";
    };

    return { body, onSubmit };
  }
}
// export default {
//   data() {
//     body: "";
//   },
//   methods: {
//     onSubmit() {
//       this.$emit("onSubmit", {
//         id: Math.round(Math.random() * 30),
//         avatar: `https://avatars.dicebear.com/api/croodles/${Date.now()}.svg`,
//         body: this.item,
//         date: new Date(Date.now()).toLocaleString(),
//         likes: 0,
//       });
//       this.item = "";
//     },
//   },
// };
</script>
