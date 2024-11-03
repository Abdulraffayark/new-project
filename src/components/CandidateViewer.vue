<template>
  <div class="p-4 border rounded-lg shadow-md mx-auto w-[80%] min-h-[150px]">
    <div class="flex justify-between items-center mb-4">
      <button @click="prevCandidate" class="text-gray-500 hover:text-gray-800">
        &larr;
      </button>
      <span>{{ currentIndex + 1 }} out of {{ candidates.length }}</span>
      <button @click="nextCandidate" class="text-gray-500 hover:text-gray-800">
        &rarr;
      </button>
      <button @click="closeCard" class="text-gray-500 hover:text-red-600 ml-auto">
        &times;
      </button>
    </div>

    <div class="flex items-center mb-4">
      <img :src="currentCandidate.photo" alt="Candidate Photo" class="w-16 h-16 rounded-full mr-4" />
      <div>
        <h2 class="text-lg font-semibold">{{ currentCandidate.name }}</h2>
        <p class="text-sm text-gray-500">{{ currentCandidate.origin }}</p>
      </div>
    </div>

    <div class="flex items-center mb-4">
      <span class="text-yellow-500">★ {{ currentCandidate.rating }}</span>
      <span :class="statusClass" class="ml-2 text-sm px-2 py-1 rounded-lg">
        {{ currentCandidate.status }}
      </span>
      <button class="ml-4 py-1 px-3 bg-green-600 text-white rounded-md hover:bg-green-700">
        Send Email
      </button>
    </div>

    <div class="flex flex-col sm:flex-row justify-between text-sm text-gray-600 mb-2">
      <span class="mb-0">
        <strong>Applied at:</strong> {{ currentCandidate.appliedAt }}
      </span>
      <span class="mt-0 sm:mt-0">
        <strong>Job Applied:</strong> {{ currentCandidate.jobApplied }}
      </span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentIndex: 0,
      candidates: [
        {
          name: "Kristi Sipes",
          origin: "Career Site",
          rating: 3.5,
          status: "Active",
          appliedAt: "13 October, 2023",
          jobApplied: "Research and Development",
          photo: "https://via.placeholder.com/50"
        },
        {
          name: "Alex Johnson",
          origin: "LinkedIn",
          rating: 4.0,
          status: "Inactive",
          appliedAt: "15 October, 2023",
          jobApplied: "Software Engineer",
          photo: "https://via.placeholder.com/50"
        },
      ]
    };
  },
  computed: {
    currentCandidate() {
      return this.candidates[this.currentIndex];
    },
    statusClass() {
      return this.currentCandidate.status === "Active"
        ? "bg-green-100 text-green-800"
        : "bg-red-100 text-red-800"; // Red for inactive status
    }
  },
  methods: {
    nextCandidate() {
      if (this.currentIndex < this.candidates.length - 1) {
        this.currentIndex++;
      }
    },
    prevCandidate() {
      if (this.currentIndex > 0) {
        this.currentIndex--;
      }
    },
    closeCard() {
      this.$emit("close");
    }
  }
};
</script>

<style scoped>
/* Add any custom styles here */
</style>
