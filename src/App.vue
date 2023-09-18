<script>
import StarComponent from "./StarComponent.vue";

export default {
  data() {
    return {
      starCraft: [{

      }],
    }
  },
  components: {
    StarComponent,
  },
  computed: {

  },
  methods: {
    starGenerator() {
      setTimeout(async () => {
        for (var i = 0; i < (Math.random() * 600000); i++) {
          this.starCraft[i] = {
            params: [
              Math.random() * 10,
              Math.random() * 20,
              Math.random() * 3000,
              Math.random() * 3000
            ],
            height: (Math.random() * 20),
            width: (Math.random() * 20),
          };

        }

        this.starGenerator();
      }, 3000);
    }
  },
  mounted() {
    this.starGenerator();

  }
}

</script>

<template>
  <body class="body">
    <div class="grid" v-for="star in starCraft">
      <div class="grid-item">
        <StarComponent :height="star.height" :width="star.width" :dataSource="star.params"></StarComponent>
      </div>
    </div>

  </body>
</template>

<style scoped>
.body {
  background-color: #2e4482;
  max-width: 100vw;
  max-height: 100vh;
  flex-flow: row wrap;
  display: flex;
}

.grid-item {
  display: grid;
  flex: 0 0 auto;
}

.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-flow: row;


  margin: 0 auto;

}
</style>
