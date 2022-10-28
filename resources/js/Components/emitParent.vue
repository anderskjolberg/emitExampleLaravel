<template>
  <div>
    <div class="py-1">
      <h3 class="text-xl font-semibold leading-tight text-gray-800 mb-5">
        Parent class
      </h3>
      <div class="mx-auto max-w-7xl lg:max-w-none sm:px-6 lg:px-8 mt-2">
        <div
          class="
            mx-auto
            overflow-hidden
            bg-white
            shadow-xl
            max-w-7xl
            sm:rounded-lg
            outline-gray-100 outline-1 outline
          "
        >
          <br />
          <button class="bg-slate-400 p-2 rounded-md ml-5" @click="logTest">
            Kall funskjon i child
          </button>
          <br />
          <br />
        </div>
        <br />
        <h3 class="text-xl font-semibold leading-tight text-gray-800 mb-5">
          Childs:
        </h3>
        <div
          class="
            overflow-hidden
            bg-white
            shadow-xl
            sm:rounded-lg
            outline-gray-100 outline-1 outline
          "
        >
          <div class="mt-6 text-gray-500">
            <!-- emitData som sendes fra child sendes til setData i denne (parent) filen -->
            <emOne @emitData="setData" />
          </div>
        </div>
        <div
          class="
            overflow-hidden
            bg-white
            shadow-xl
            sm:rounded-lg
            mt-2
            outline-gray-100 outline-1 outline
          "
        >
          <div class="mt-6 text-gray-500">
            <emTwo :parentData="data" ref="childComponent" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { defineComponent } from "vue";
import emOne from "@/Components/emitChildFirst.vue";
import emTwo from "@/Components/emitChildTwo.vue";

export default defineComponent({
  components: {
    emOne,
    emTwo,
  },
  data() {
    return {
      data: null,
    };
  },
  methods: {
    logTest() {
      var child = this.$refs.childComponent;
      // om det er data i Transit og du ikke har tilgang, bruk nextTick, da dataen er mest sansynlig tilgjengelig i neste frame
      this.$nextTick(() => {
        child.childClicked();
      });
    },
    setData(e) {
      this.data = e;
    },
  },
});
</script>