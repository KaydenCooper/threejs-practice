<template>
  <div class="viewport" />
</template>


<script>
import { mapMutations, mapActions } from "vuex";
export default {
  data() {
    return {
      height: 0,
    };
  },
  mounted() {
    this.INIT({
      width: this.$el.offsetWidth,
      height: this.$el.offsetHeight,
      el: this.$el,
    }).then(() => {
      this.ANIMATE();
      window.addEventListener("resize", () => {
        this.RESIZE({
          width: this.$el.offsetWidth,
          height: this.$el.offsetHeight,
        });
      });
    });
  },
  computed: {},
  methods: {
    ...mapMutations(["RESIZE"]),
    ...mapActions(["INIT", "ANIMATE"]),
  },
  components: {},
};
</script>


<style scoped>
.viewport {
  height: 100%;
  width: 100%;
}
</style>