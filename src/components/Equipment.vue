<template>
  <div id="Equipment">
    <div class="wrap">
      <div class="cards">
        <div class="card shop">
          <h1 class="shop-title">Shop</h1>
          <ul class="shop-menus">
            <li>
              <p>Helmet</p>
              <ItemSelect
                :isCleared="isCleared"
                :equipment="equipment.helmets"
                :label="'helmets'"
                @selectedItem="saveSelectedItem"
                @removeSelectedItem="removeSelectedItem"
              />
            </li>
            <li>
              <p>Chest</p>
              <ItemSelect
                :isCleared="isCleared"
                :equipment="equipment.chests"
                :label="'chests'"
                @selectedItem="saveSelectedItem"
                @removeSelectedItem="removeSelectedItem"
              />
            </li>
            <li>
              <p>Gloves</p>
              <ItemSelect
                :isCleared="isCleared"
                :equipment="equipment.gloves"
                :label="'gloves'"
                @selectedItem="saveSelectedItem"
                @removeSelectedItem="removeSelectedItem"
              />
            </li>
            <li>
              <p>Boots</p>
              <ItemSelect
                :isCleared="isCleared"
                :equipment="equipment.boots"
                :label="'boots'"
                @selectedItem="saveSelectedItem"
                @removeSelectedItem="removeSelectedItem"
              />
            </li>
            <li>
              <p>Sword</p>
              <ItemSelect
                :isCleared="isCleared"
                :equipment="equipment.swords"
                :label="'swords'"
                @selectedItem="saveSelectedItem"
                @removeSelectedItem="removeSelectedItem"
              />
            </li>
          </ul>

          <div class="delim"></div>

          <h3 class="cost">Equipment cost: {{totalStats.cost}}</h3>

          <button class="remove-items" @click="cleanCharacter">Снять снаряжение</button>
        </div>

        <div class="card character">
          <Character :itemSet="saveItemSet" :heroImg="heroImg" :nakedHeroImg="nakedHeroImg" />

          <div class="stats">
            <p class="stats-name-label">Name:</p>
            <p class="stats-name">{{heroName}}</p>
            <p class="stats-label">Stats:</p>
            <p class="stats-health">{{parseInt(baseHealth) + parseInt(totalStats.health)}}</p>
            <p class="stats-armor">{{parseInt(baseArmor) + parseInt(totalStats.armor)}}</p>
            <p class="stats-attack">{{parseInt(baseAttack) + parseInt(totalStats.attack)}}</p>

            <svg
              class="stats-icon-health"
              width="16"
              height="14"
              viewBox="0 0 16 14"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M16 4.06457C16 -1.35484 8 -1.35487 8 4.06457C8 -1.35478 0 -1.35484 0 4.06457C0 9.48397 5.33333 12.6452 8 14C10.6667 12.6453 16 9.48397 16 4.06457Z"
                fill="#FF0000"
              />
            </svg>

            <svg
              class="stats-icon-armor"
              width="17"
              height="20"
              viewBox="0 0 17 20"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                fill-rule="evenodd"
                clip-rule="evenodd"
                d="M8.5 19C15 15.5 16 7 16 6C16 5 16 4 14.5 4C13.5 4 12.5 3.25 11.5 2.5C10.5 1.75 9.5 1 8.5 1V19Z"
                fill="#2750B8"
              />
              <path
                fill-rule="evenodd"
                clip-rule="evenodd"
                d="M5.5 2.5C4.5 3.25 3.5 4 2.5 4C1 4 1 5 1 6C1 7 2 15.5 8.5 19C15 15.5 16 7 16 6C16 5 16 4 14.5 4C13.5 4 12.5 3.25 11.5 2.5C10.5 1.75 9.5 1 8.5 1C7.5 1 6.5 1.75 5.5 2.5Z"
                stroke="#2750B8"
              />
            </svg>

            <svg
              class="stats-icon-attack"
              width="21"
              height="20"
              viewBox="0 0 21 20"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                fill-rule="evenodd"
                clip-rule="evenodd"
                d="M18.8581 0.378409C19.22 0.257862 19.5818 0.13734 19.9434 0.0169253C19.9587 0.0118469 19.9756 0.00676845 20.0027 0L19.9977 0.0150203C19.8979 0.312646 19.8014 0.600582 19.7065 0.886882C19.5035 1.49574 19.3006 2.10501 19.0976 2.71429C18.8927 3.32956 18.6877 3.94482 18.4828 4.55966C18.4726 4.59182 18.4591 4.62059 18.432 4.64429C17.6739 5.33487 16.9165 6.02622 16.1589 6.71782C15.7968 7.04833 15.4347 7.37889 15.0724 7.70945C14.6203 8.12255 14.1679 8.53523 13.7154 8.9479C13.2632 9.36033 12.811 9.77277 12.3592 10.1856C11.8845 10.6189 11.4093 11.0522 10.9341 11.4855C10.459 11.9188 9.98378 12.352 9.50902 12.7853C9.38453 12.899 9.26005 13.0126 9.13558 13.1261C8.77271 13.4572 8.41007 13.788 8.04837 14.1207C8.00945 14.1563 7.9976 14.1461 7.9739 14.1089C7.84447 13.9042 7.71462 13.6999 7.58477 13.4956C7.45482 13.2911 7.32487 13.0867 7.19534 12.8818C7.17672 12.8513 7.15303 12.8277 7.12087 12.8073C6.96533 12.7088 6.81003 12.6101 6.6548 12.5114C6.40463 12.3523 6.15461 12.1933 5.90394 12.0356C5.85655 12.0051 5.84809 11.9882 5.8904 11.9425C6.19737 11.6086 6.50338 11.2729 6.80915 10.9374C6.908 10.8289 7.00682 10.7205 7.10564 10.6121L8.54259 9.03809C8.79264 8.76419 9.0429 8.4903 9.29321 8.21633C9.77145 7.69292 10.2499 7.16925 10.7276 6.64486L12.7841 4.39041C13.1708 3.96644 13.558 3.54246 13.9451 3.11848C14.3323 2.6945 14.7195 2.27052 15.1062 1.84655C15.1203 1.83075 15.1352 1.81533 15.15 1.79991C15.1797 1.76907 15.2095 1.73822 15.2331 1.70437C15.3262 1.57235 15.4583 1.50804 15.6089 1.45896C16.6922 1.09996 17.7755 0.739067 18.8581 0.378409ZM6.57757 13.3642C6.59788 13.3794 6.6165 13.3947 6.63173 13.4167C6.81977 13.6828 7.00781 13.9491 7.19587 14.2154C7.83893 15.1259 8.48221 16.0367 9.12652 16.9456C9.15359 16.9845 9.1519 17.0014 9.11974 17.0336C8.80832 17.3416 8.49859 17.6514 8.19055 17.9628C8.1567 17.9983 8.14146 17.9966 8.10761 17.9628C7.84078 17.6953 7.5734 17.4278 7.30592 17.1601C6.90492 16.7589 6.50368 16.3575 6.10366 15.9554C6.06812 15.9199 6.0495 15.9182 6.00888 15.9504C5.40853 16.4239 4.80699 16.8968 4.20532 17.3698C3.78756 17.6982 3.36973 18.0267 2.95218 18.3554C2.94844 18.3586 2.94452 18.3614 2.94067 18.3642C2.92361 18.3765 2.90773 18.388 2.91325 18.4198C2.96403 18.6821 2.9014 18.9275 2.7897 19.1611C2.51889 19.7298 1.94513 20.0327 1.37813 19.9972C0.704505 19.9549 0.195055 19.4725 0.0478063 18.9038C-0.165451 18.0829 0.355845 17.2587 1.19195 17.0945C1.26473 17.0793 1.33751 17.0708 1.41198 17.0674C1.42308 17.068 1.43451 17.0677 1.44595 17.0674C1.47117 17.0667 1.49649 17.0661 1.51861 17.0742C1.5897 17.0996 1.62693 17.0708 1.66924 17.0167C2.10883 16.456 2.54924 15.8962 2.98989 15.336C3.18378 15.0896 3.37771 14.843 3.57164 14.5963C3.72905 14.3949 3.88645 14.1935 4.04555 13.9938C4.0794 13.9532 4.0794 13.9329 4.04047 13.8939C3.77371 13.6279 3.50722 13.3615 3.24079 13.0952C2.84118 12.6958 2.44169 12.2965 2.0416 11.8985C2.00098 11.8578 2.00437 11.8375 2.04329 11.7986C2.35133 11.4956 2.65599 11.1893 2.95895 10.8829C2.99619 10.8457 3.01819 10.8474 3.05712 10.8762C3.64322 11.2906 4.22974 11.705 4.81627 12.1194C5.40351 12.5343 5.99075 12.9493 6.57757 13.3642Z"
                fill="#1C6565"
              />
            </svg>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Character from "./Character";
import ItemSelect from "./ItemSelect";

export default {
  name: "Equipment",
  components: {
    Character,
    ItemSelect
  },
  data: () => ({
    heroName: "", //
    baseAttack: 0, //
    baseHealth: 0, // Базовые хар-ки, берутся из JSONа
    baseArmor: 0, //
    heroImg: "", //
    nakedHeroImg: "", //
    equipment: {}, //
    selectedItems: {},
    selectedHelmet: "", //
    selectedChest: "", //
    selectedGloves: "", //  Хранят выбранную экипировку
    selectedBoots: "", //
    selectedSword: "", //
    isCleared: false
  }),
  methods: {
    // Снимаем всю экипировку с персонажа
    cleanCharacter() {
      this.isCleared = !this.isCleared
              
      this.selectedHelmet = "";
      this.selectedChest = "";
      this.selectedGloves = "";
      this.selectedBoots = "";
      this.selectedSword = "";
      this.selectedItems = {};
    },
    saveSelectedItem(data) {
      this.selectedItems[data.label] = data.value;

      if (this.selectedItems["helmets"])
        this.selectedHelmet = this.selectedItems["helmets"];
      if (this.selectedItems["chests"])
        this.selectedChest = this.selectedItems["chests"];
      if (this.selectedItems["gloves"])
        this.selectedGloves = this.selectedItems["gloves"];
      if (this.selectedItems["boots"])
        this.selectedBoots = this.selectedItems["boots"];
      if (this.selectedItems["swords"])
        this.selectedSword = this.selectedItems["swords"];
    },
    removeSelectedItem(data) {
      this.selectedItems[data.label] = "";
      this.saveState();
    },
    saveState() {
      if (this.selectedHelmet)
        this.selectedHelmet = this.selectedItems["helmets"];
      if (this.selectedChest) 
        this.selectedChest = this.selectedItems["chests"];
      if (this.selectedGloves)
        this.selectedGloves = this.selectedItems["gloves"];
      if (this.selectedBoots) 
        this.selectedBoots = this.selectedItems["boots"];
      if (this.selectedSword) 
      this.selectedSword = this.selectedItems["swords"];
    }
  },
  
  computed: {
    /*
    Это такой жуткий костыль который следит за изменениями в показателях выбранных предметов
    */
    totalStats() {
      const items = [
        this.selectedHelmet,
        this.selectedChest,
        this.selectedGloves,
        this.selectedBoots,
        this.selectedSword
      ];

      let total = {
        cost: 0,
        health: 0,
        armor: 0,
        attack: 0
      };

      for (let item of items) {
        if (!isNaN(item.price)) total.cost += parseInt(item.price);

        if (!isNaN(item.health)) total.health += parseInt(item.health);

        if (!isNaN(item.armor)) total.armor += parseInt(item.armor);

        if (!isNaN(item.attack)) total.attack += parseInt(item.attack);
      }

      return total;
    },
    /*Проверяем есть ли на персе шлем, чтобы убрать хвост */
    isNaked() {
      if (this.selectedHelmet != "") {
        return false;
      } else {
        return true;
      }
    },
    saveItemSet() {
      let itemSet = {};
      itemSet["helmet"] = this.selectedHelmet.img;
      itemSet["chest"] = this.selectedChest.img;
      itemSet["gloves"] = this.selectedGloves.img;
      itemSet["boots"] = this.selectedBoots.img;
      itemSet["sword"] = this.selectedSword.img;
      return itemSet;
    }
  },
  //Подгрузка JSONа с данными
  created() {
    axios
      .get("https://hrp-serv.herokuapp.com/json")
      .then(response => {
        const equipJson = response.data;
        this.heroName = equipJson.person.name;
        this.baseAttack = equipJson.person.attack;
        this.baseHealth = equipJson.person.health;
        this.baseArmor = equipJson.person.armor;
        this.nakedHeroImg = equipJson.person.img;
        this.heroImg = equipJson.person["alt-img"];
        this.equipment = equipJson.equipment;
      })
      .catch(error => {
        console.log(error);
      });
  },
};
</script>


<style scoped>
.wrap {
  margin-left: auto;
  margin-right: auto;
  margin-top: 10vh;
  width: 1024px;
  height: 768px;
  background-color: #1c6565;
}

.shop-title {
  margin-top: 27px;
  margin-bottom: 38px;
  font-family: Roboto;
  font-style: normal;
  font-weight: bold;
  font-size: 24px;
  line-height: 28px;
  text-align: center;
  text-transform: uppercase;

  color: #000000;
}

.cards {
  display: grid;
  grid-gap: 30px;
  grid-template-columns: 1fr 1fr;
  align-content: center;
  justify-items: center;

  max-width: 770px;
  width: 100%;
  padding: 84px 127px;
}
.card {
  width: 370px;
  height: 551px;
  background: #f9e88e;
  border-radius: 4px;
}

.shop-menus {
  display: grid;
  grid-template-columns: 1fr;
  grid-row-gap: 20px;
}
.shop-menus li {
  display: grid;
  grid-template-columns: 1fr 4fr;
  grid-column-gap: 21px;
  margin-left: 50px;
  margin-right: 50px;
}

.shop-menus li p {
  font-family: Roboto;
  font-style: normal;
  font-weight: 500;
  font-size: 14px;
  text-align: center;
  color: #000000;
  display: flex;
  align-items: center;
}

.cost {
  margin-top: 25px;
  margin-left: 50px;
  font-family: Roboto;
  font-style: normal;
  font-weight: 500;
  font-size: 14px;
  color: #000000;
}

.shop-select {
  background-color: #fff;
}

.select {
  background-color: #fff;
  cursor: pointer;
}

.vs__actions svg {
  width: 8px;
  height: 4px;
}

.delim {
  width: 270px;
  margin-left: auto;
  margin-right: auto;
  margin-top: 25px;
  border: 1px solid #727272;
}

.remove-items {
  width: 140px;
  height: 30px;
  margin-top: 20px;
  margin-left: calc(370px / 2 - 140px / 2);
  margin-right: auto;
  background-color: #fff;
  border: 1px solid rgba(60, 60, 60, 0.26);
  border-radius: 4px;
}

li {
  list-style-type: none;
}

.character {
  position: relative;
}

/*Stats*/
.stats {
  display: grid;
  grid-column-gap: 30px;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 1fr 1fr 1fr 1fr;
  width: 143px;
  height: 100px;
  margin-top: 394px;
  margin-left: 100px;
}

.stats p {
  font-family: Roboto;
  font-style: normal;
  font-weight: 500;
  font-size: 14px;
  line-height: 16px;
}
.stats-label {
  grid-column: 1/2;
}
.stats-health {
  grid-column: 2/3;
}
.stats-armor {
  grid-column: 2/3;
}
.stats-attack {
  grid-column: 2/3;
}

.stats-icon-health {
  width: 16px;
  height: 14px;
  grid-row: 2/3;
  grid-column: 3/4;
}
.stats-icon-armor {
  width: 15px;
  height: 18px;
  grid-row: 3/4;
  grid-column: 3/4;
}
.stats-icon-attack {
  width: 18px;
  height: 18px;
  grid-row: 4/5;
  grid-column: 3/4;
}
</style>
