<template>
  <v-card>
    <v-flex xs12 sm10>
      <v-tree url="/item/category/of/parent" isEdit @handAdd="handleAdd"></v-tree>
    </v-flex>
  </v-card>
</template>

<script>
  export default {
    name: "category",
    data() {
      return {
        isEdit: true
      }
    },
    methods: {
      handleAdd(node) {
        axios.post('/user', {
          firstName: 'Fred',
          lastName: 'Flintstone'
        })
                .then(function (response) {
                  console.log(response);

                })
                .catch(function (error) {
                  console.log(error);
                });
        console.log("add .... ");
        console.log(node);
      },
      handleEdit(id, name) {
        console.log("edit... id: " + id + ", name: " + name)
      },
      handleDelete(id) {
        console.log("delete ... " + id)
      },
      handleClick(node) {
        console.log(node)
      }
    }
  };
</script>

<style scoped>

</style>
