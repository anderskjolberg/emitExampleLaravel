<template>
  <div class="grid grid-cols-2 gap-2">
    <div class="p-5">
      <h3>Child 1</h3>
      <label for="filterDrop">Filter roles: </label>
      <!-- Når verdien endres kjøres sendFields funksjonen -->
      <!-- optionValue data er bindet fra select modellen til javascript variabel -->
      <select v-model="optionValue" @change="sendFields" name="filterDrop" id="filterDrop">
        <option value="1">All</option>
        <option value="2">Superintenden</option>
        <option value="3">Diving Supervisor</option>
        <option value="4">Project Manager</option>
        <option value="5">Mechanic</option>
        <option value="6">Trenching Specialist</option>
        <option value="7">Diver</option>
        <option value="8">DMT</option>
        <option value="9">DDC Operator</option>
        <option value="10">Vesselmaster</option>
        <option value="11">Deck Hand</option>
        <option value="12">RHIB operator</option>
        <option value="13">Rigger</option>
        <option value="14">Beach Master</option>
      </select>
    </div>
    <!-- <div class="pt-5"> -->
      <!-- <button class="bg-slate-400 p-2 rounded-md" @click="logTest">Log out option</button> -->
    <!-- </div> -->
  </div>
</template>
<script>
import { defineComponent } from "vue";
export default defineComponent({
  //Datafelt som skal sendes
  emits: ["emitData"],
  components: {
  },
  data() {
    return {
      optionValue: "",
    };
  },
  methods: {
    // logTest() {
      // console.log(propName);
      // this.$nextTick(() => {
      //   this.sendFields(propName)
      // });
    //   console.log(this.optionValue);
    // },
    sendFields(){
      // fuksjonen som sender datafelt, i dette tilfellet en data variabel gjennom emit emitData til parent som kaller komponentet
      this.$emit("emitData", this.optionValue);
    }
  },
});
</script>

