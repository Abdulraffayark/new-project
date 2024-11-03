<template>
  <div class="min-h-screen bg-gray-100 flex items-center justify-center">
    <CandidateViewer @close="closeCard" v-if="showCard" />
  </div>
</template>

<script>
import CandidateViewer from './components/CandidateViewer.vue';

export default {
  components: 
  {  
    CandidateViewer
  },
  data() {
    return {
      showCard: true
    };
  },
  methods: {
    closeCard() {
      this.showCard = false;
    }
  }
};
</script>
