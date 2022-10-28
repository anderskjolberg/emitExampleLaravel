<template>
  <div class="grid grid-cols-2 gap-2">
    <div class="p-5">
      Child 2
      <br />
      <p>Data som mottas:</p>
      <!-- viser prop data -->
      {{this.parentData}}
      <p v-if="this.optionValue">Parent: show this field</p>
    </div>
  </div>
</template>
<script>
import { defineComponent } from "vue";
export default defineComponent({
  // props er data sendt fra parent
  props: ["parentData"],
  components: {
  },
  data() {
    return {
      optionValue: false,
    };
  },
  methods: {
    childClicked(){
      if(this.optionValue){
        this.optionValue = false;
      }else{
        this.optionValue = true;
      }
    }
  },
});
</script>

