<template>
  <div class="story-grid">
    <card
      v-for="card in storyCards"
      :key="card.id"
      :title="card.title"
      :subtitle="card.subtitle"
      :photo="card.photo"
      :href="storyHref(card.id)"
    />
  </div>
</template>

<script>
import Card from '@/components/ui/Card';

export default {
  components: {
    card: Card,
  },

  methods: {
    storyHref(id) {
      return 'stories/' + id;
    },
  },
  computed: {
    storyCards() {
      return this.$store.getters['data/stories/getStories'];
    },
  },
};
</script>

<style scoped>
.story-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(2, 1fr);
  row-gap: 50px;
  column-gap: 20px;
  margin: -10px;
}

@media screen and (max-width: 1280px) {
  .story-grid {
    row-gap: 40px;
  }
}

@media screen and (max-width: 1024px) {
  .story-grid {
    column-gap: 10px;
    row-gap: 25px;
  }
}

@media screen and (max-width: 768px) {
  .story-grid {
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(3, 1fr);
    grid-column-gap: 0;
    grid-row-gap: 20px;
  }
}
@media screen and (max-width: 455px) {
  .story-grid {
    grid-template-columns: 1fr;
    grid-template-rows: repeat(6, 1fr);
    grid-column-gap: 10px;
    grid-row-gap: 10px;
  }
}
</style>
