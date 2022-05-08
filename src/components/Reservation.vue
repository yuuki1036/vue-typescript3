<script setup lang="ts">
import Card from './Card.vue';
import Badge from './Badge.vue';
import { ref } from 'vue';
import MosaicReservation from './MosaicReservation.vue';
import ReservationList from './ReservationList.vue';

const isListVisible = ref<boolean>(true)
const isDialogOpen = ref<boolean>(false)

const onClickButton = () => {
  // isListVisible.value = !isListVisible.value;
  isDialogOpen.value = !isDialogOpen.value
}
</script>

<template>
<div class="container">
  <Card class="menu-card">
    <span>Badges</span>
    <div class="badges">
      <Badge class="vip-badge">
        <span>VIP</span>
      </Badge>
      <Badge class="normal-badge">
        <span>NORMAL</span>
      </Badge>
    </div>
  </Card>
<component :is="ReservationList" />
  <!-- <div v-if="isListVisible">
    <ReservationList/>
  </div>
  <div v-if="!isListVisible">
  <MosaicReservation/>
  </div> -->

  <button @click="onClickButton">change</button>
  <teleport to="body">
    <dialog :open="isDialogOpen" class="dialog">
      <span>Dialog</span>
    </dialog>
  </teleport>
</div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.dialog {
  position: absolute;
  top:0;
  left:0;
  right: 0;
  bottom:0;
  height: 300px;
  width: 400px;
  margin: auto;

}
.menu-card {
  width: 300px;
  height: 80px;
  background-color: #ccc;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 24px;
  border-radius: 8px;
  box-shadow: 4px 4px 4px rgb(211, 211, 211);
}
.vip-badge {
  background-color: #810036;
  color: white;
}
.normal-badge {
  background-color: #002c8a;
  color: white;
}
.badges {
display:  flex;
justify-content: space-between;
width: 60%;
}
</style>