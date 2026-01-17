<template>
  <div id="topGrid">
    <div id="leftTopDiv">
      <div id="leftTopFlex">
        <div class="item" v-for="item in userSelected">
          <Item :id="item.id" :name="item.name" @remove="handleRemoveUserItem" :top="true"/>
        </div>
      </div>
      <p>Selected: {{ userSelected.length }} / 6</p>
    </div>
    <div id="selectedItem">
      <h2>{{ storeSelected?.name }}</h2>
    </div>
  </div>
  <div id="bottomGrid">
    <div id="leftBottomGrid">
      <div class="item" v-for="item in userData">
        <Item :id="item.id" :name="item.name" @add="handleAddUserItem" :top="false"/>
      </div>
      
    </div>
    <div id="rightBottomGrid" >
      <div class="item" v-for="item in storeData">
        <Item :id="item.id" :name="item.name" @add="handleAddStoreItem" :top="false" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import Item from './components/Item.vue';
// define changing refs
const userSelected = ref([])
const storeSelected = ref({name: 'Selected'})
// define functions to handle Item.vue emits
// add up to 6 items to userSelected array alert if trying to add more displayed at top left corner
function handleAddUserItem(id) {
  if (userSelected.value.length < 6) {
    var selectedItem = userData.find(obj => {
      return obj.id === id
    })
    userSelected.value.push(selectedItem)
  } else {
    alert('Too many items! Please remove some to add more.')
  }
}
// display chosen store item in top right corner
function handleAddStoreItem(id) {
  var selectedItem = storeData.find(obj => {
      return obj.id === id
    })
  storeSelected.value = selectedItem
}
// remove an item from userSelected array
function handleRemoveUserItem(id) {
  let filteredArray = userSelected.value.filter(obj => {
    return obj.id != id
  })
  userSelected.value = filteredArray
}
// declare data variables
  const userData = [
    {
        "id": 1,
        "name": "Shoes 1"
    },
    {
        "id": 2,
        "name": "Shoes 2"
    },
    {
        "id": 3,
        "name": "Shoes 3"
    },
    {
        "id": 4,
        "name": "Shoes 4"
    },
    {
        "id": 5,
        "name": "T-shirt 1"
    },
    {
        "id": 6,
        "name": "T-shirt 2"
    },
    {
        "id": 7,
        "name": "T-shirt 3"
    },
    {
        "id": 8,
        "name": "T-shirt 4"
    }
]

const storeData = [
    {
        "id": 11,
        "name": "Jacket 1"
    },
    {
        "id": 12,
        "name": "Jacket 2"
    },
    {
        "id": 13,
        "name": "Jacket 3"
    },
    {
        "id": 14,
        "name": "Jacket 4"
    },
    {
        "id": 15,
        "name": "Hoodie 1"
    },
    {
        "id": 16,
        "name": "Hoodie 2"
    },
    {
        "id": 17,
        "name": "Hoodie 3"
    },
    {
        "id": 18,
        "name": "Hoodie 4"
    }
]
</script>

<style scoped>
  /* define top blocks layout */
  #topGrid {
    display: flex;
    justify-content: space-between;
    margin-bottom: 2em;
  }
  /* define left top box */
  #leftTopDiv {
    border: 3px solid black;
    text-align: center;
  }
  /* define top left items flex */
  #leftTopFlex {
    display: flex;
    gap: 1em;
    padding: 1em;
    min-width: 10em;
  }
  /* define top right box */
  #selectedItem {
    padding: 1em;
    border: 3px solid black;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  /* define bottom boxes layout */
  #bottomGrid {
    display: grid;
    grid-template-columns: auto auto;
    column-gap: 1em;
  }
  /* define bottom item grids */
  #leftBottomGrid,
  #rightBottomGrid {
    display: grid;
    grid-template-columns: auto auto auto auto;
    border: 3px solid black;
    gap: 1em;
    padding: 1em;
    text-align: center;
  }
  /* define item wrapper */
  .item {
    border: 3px solid black;
    padding: 1em;
  }
</style>
