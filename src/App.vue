<template>
  <div class="wrapper">
    <div class="wrapper-context">
      <div class="view">
        <div class="container">
          <Form @onSubmit="handleSubmit" />
          <List :items="items" />
        </div>
      </div>
    </div>
  </div>
</template>


<script>
import {ref} from 'vue'
import List from "@/components/List.vue";
import Form from "@/components/Form.vue";

export default {
  components: { Form, List },
  setup() {
    const items = ref([
      {
        id: 1,
        avatar: `https://avatars.dicebear.com/api/croodles/1.svg`,
        body: "hello",
        date: new Date(Date.now()).toLocaleString(),
        likes: 0,
      },
    ])

    const handleSubmit = (item) => items.value.push(item);
    

    return {
      items,
      handleSubmit
    };
  },
};

// export default {
//   components: { Form, List },
//   data() {
//     return {
//       items: [
//         {
//           id: 1,
//           avatar: `https://avatars.dicebear.com/api/croodles/1.svg`,
//           body: "hello",
//           date: new Date(Date.now()).toLocaleString(),
//           likes: 12,
//         },
//       ],
//     };
//   },
//   methods: {
//     handleSubmit(item) {
//       console.log(item);
//       this.items.push(item);
//     },
//   },
// };
</script>
