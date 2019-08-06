<template>
  <div class="character">
    <img v-if="isNaked" :src="nakedHeroImg" class="hero" />
    <img v-else :src="heroImg" class="hero" />

    <img :src="itemSet.helmet" class="equip-item helmet" />
    <img :src="itemSet.chest" class="equip-item chest" />
    <img :src="itemSet.gloves" class="equip-item gloves" />
    <img :src="itemSet.boots" class="equip-item boots" />
    <img :src="itemSet.sword" class="equip-item sword" />
  </div>
</template>

<script>
export default {
  props:['itemSet', 'heroImg', 'nakedHeroImg'],
  data: () => ({

  }),
  computed:{
    isNaked() {
      if (this.itemSet.helmet != undefined) {
        return false;
      } else {
        return true;
      }
    },
  }
};
</script>

<style scoped>
.hero {
  position: absolute;
  top: 41px;
  left: 118px;
}
/*Items*/
.helmet {
  position: absolute;
  top: 50px;
  left: 130px;
}

.chest {
  position: absolute;
  top: 126px;
  left: 135px;
}

.gloves {
  position: absolute;
  top: 193px;
  left: 80px;
}

.boots {
  position: absolute;
  top: 293px;
  left: 120px;
}
/*Меч исходного размера вылезал за край окна*/
.sword {
  width: 70%;
  position: absolute;
  top: 235px;
}

</style>
