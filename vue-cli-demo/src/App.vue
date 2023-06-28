<template>
  <div>
    <input type="text" v-model="inputVal">
    <button @click="handleAddItem" class="button">提交</button>
    <ul>
      <list-item 
      v-for="item in list"
       :key="index"
       :msg="item"
      />
    </ul>
  </div>
</template>

<script>
import { reactive, ref } from 'vue';
import ListItem from './components/ListItem.vue'

export default {
  name: 'App',
  components:{
    ListItem
  },
  setup() {
    const inputVal = ref('')
    const list = reactive([])
    const handleAddItem = () => {
      list.push(inputVal.value)
      inputVal.value = ''
    }
    return { list, handleAddItem, inputVal }
  }
}
</script>

<style>
  .button{
    margin-left: 20px;
  }

</style>
