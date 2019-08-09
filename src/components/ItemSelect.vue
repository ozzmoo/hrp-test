<template>
  <div class="select-wrap">
    <select @change="returnData" v-model="value" class="select">
      <option
        v-for="item in equipment"
        :value="item"
        :key="item.id"
        class="select-item"
      >{{item.name}}</option>
    </select>
    <button @click="removeItem" class="remove-item">X</button>
  </div>
</template>


<script>
export default {
  props: ["equipment", "label", "isCleared"],
  data: () => ({
    value: ""
  }),
  methods: {
    returnData() {
      this.$emit("selectedItem", {
        label: this.label,
        value: this.value
      });
    },
    removeItem() {
      this.value = "";
      this.$emit("removeSelectedItem", {
        label: this.label,
        value: this.value
      });
    }
  },
  watch: {
    isCleared: function(newV, oldV) {
      if (newV != oldV) {
        this.value = "";
      }
    },
    
  },
};
</script>

<style scoped>
select {
  width: 200px;
  height: 36px;
  border-radius: 5px;
  outline: none;
}

.select-wrap {
  margin-right: 0px;
  margin-left: auto;
  height: 36px;
  width: 230px;
}

.remove-item {
  height: 30px;
  width: 30px;
  text-align: center;
  font-size: 14px;
  line-height: 14px;
  background-color: rgba(255, 255, 255, 0);
  border: none;
  outline: none;
}
.remove-item:active {
  background-color: rgba(0, 0, 0, 0.26);
}
</style>
