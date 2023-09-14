<template>
  <div class="learning-pathways">
    <h2 class="choose-pathway">Choose Your Learning Pathway</h2>
    <div class="pathway-cards">
      <div class="pathway-card" v-for="(pathway, index) in pathways" :key="index">
        <h3>{{ pathway.title }}</h3>
        <p>{{ pathway.description }}</p>
        <button @click="toggleSelection(index)">
          {{ selectedPathways.includes(index) ? 'Deselect' : 'Select' }}
        </button>
        
        <div v-if="selectedPathways.includes(index)" class="pathway-details">
          <h4>Details</h4>
          {{ pathway.details }}
        </div>
      </div>
    </div>
    <div class="selected-count">
      Selected Pathways: {{ selectedPathways.length }}
    </div>
  </div>
</template>



<script>
export default {
  data() {
    return {
      pathways: [
        { 
          title: 'UI/UX Development', 
          description: 'Discover the art of designing user experiences.',
          details: 'UI/UX development involves creating user-friendly interfaces and optimizing user experiences.' 
        },
        { 
          title: 'Back-End Programming', 
          description: 'Unlock the world of server-side development.',
          details: 'Back-end programming deals with server-side logic, databases, and server management.' 
        },
        { 
          title: 'Integrated Development', 
          description: 'Bridge the gap between front-end and back-end.',
          details: 'Integrated development involves combining front-end and back-end technologies for a seamless user experience.' 
        }
      ],
      selectedPathways: []
    };
  },
  methods: {
    toggleSelection(index) {
      if (this.selectedPathways.includes(index)) {
        this.selectedPathways = this.selectedPathways.filter((item) => item !== index);
      } else {
        this.selectedPathways.push(index);
      }
    }
  }
};
</script>

<style scoped>
.choose-pathway {
  color: white;
}
.learning-pathways {
  background-image: url('https://wallpaperaccess.com/full/3239480.jpg');
  background-size: cover;
  background-repeat: no-repeat;
  background-attachment: fixed;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
}

.centered-text {
  text-align: center;
  margin-bottom: 20px;
}

.pathway-cards {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}

.pathway-card {
  background-color: rgba(255, 255, 255, 0.093);
  border: 1px solid black;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
  padding: 20px;
  margin: 10px;
  text-align: center;
  width: 300px;
  transition: transform 0.3s ease;
  color: white;
}

.pathway-card:hover {
  transform: scale(1.05);
}

.selected-count {
  color: white;
}
</style>

