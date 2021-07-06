<template>
<div>
  <button @click="openPopup">Открыть окно</button>
  <Popup
    :is-open="isPopupOpen"
    @ok="popupConfirmed"
    @close="isPopupOpen = false"
  >
    Вы действительно хотите освоить правильные подходы к проектированию систем
    во Vue?
<template #actions="{ confirm }">
  Напишите <input :placeholder="$options.CONFIRMATION_TEXT" v-model="confirmation"/>&nbsp;
  <button @click="confirm" :disabled="!isConfirmationCorrect">OK</button>
</template>
  </Popup>
  </div>
</template>

<script>
import Popup from "./components/Popup.vue";
export default {
  components: { Popup },
  data() {
    return { isPopupOpen: false, confirmation: "" };
  },
  computed:{
isConfirmationCorrect(){
return this.confirmation === this.$options.CONFIRMATION_TEXT
}
  },
CONFIRMATION_TEXT: "ПОДТВЕРЖДАЮ",
  

  
  methods: {
    openPopup() {
      this.confirmation = "";
      this.isPopupOpen = true;
    },

    popupConfirmed() {
      alert("Confirmed!");
      this.isPopupOpen = false;
    },
  },
};
</script>

