<template>
  <div>
    <h3>{{ currentCharacter.name }}</h3>
    <p>loading...</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      characters: [
        { name: '△' },
        { name: '▷' },
        { name: '▽' },
        { name: '◁' },
      ],
      currentIndex: 0,
    };
  },
  computed: {
    currentCharacter() {
      return this.characters[this.currentIndex];
    },
  },
  mounted() {
    this.startAutoChange();
  },
  beforeDestroy() {
    clearInterval(this.interval);
  },
  methods: {
    startAutoChange() {
      this.interval = setInterval(() => {
        this.currentIndex = (this.currentIndex + 1) % this.characters.length;
      }, 200); // Change character every 200 milliseconds (0.2 second)
    },
  },
};
</script>
