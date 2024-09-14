<template>
  <div id="app" class="container">
    <div class="card">
      <h1>Grade Calculator</h1>
      <div class="form-group">
        <label for="score">Enter your score:</label>
        <input type="number" v-model="score" placeholder="Enter score" class="input-score" />
      </div>
      <button class="btn" @click="calculateGrade">Calculate Grade</button>

      <div v-if="grade !== ''" class="result">
        <h2>Result: <span>{{ grade }}</span></h2>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      score: null,
      grade: '' 
    };
  },
  methods: {
    calculateGrade() {
      // ตรวจสอบว่ากรอกคะแนนหรือยัง
      if (this.score === null || this.score === '') {
        this.grade = 'Please enter a score';
        return;
      }

      // แปลงคะแนนเป็นตัวเลข
      const score = Number(this.score);

      // ตรวจสอบช่วงคะแนนและกำหนดเกรด
      if (score >= 80) {
        this.grade = 'A';
      } else if (score >= 70) {
        this.grade = 'B';
      } else if (score >= 60) {
        this.grade = 'C';
      } else if (score >= 50) {
        this.grade = 'D';
      } else {
        this.grade = 'F';
      }
    }
  }
};
</script>

<style scoped>

.container {
  display: flex;
  justify-content: center;
  align-items: center;
}


.card {
  background-color: white;
  padding: 40px;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  max-width: 350px;
  width: 100%;
  text-align: center;
  font-family: 'Arial', sans-serif;
}


.form-group {
  margin-bottom: 20px;
}

.input-score {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ddd;
  border-radius: 4px;
  box-sizing: border-box;
  background-color: #f5f5f5;
}


.btn {
  background-color: black;
  color: white;
  padding: 10px;
  font-size: 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  width: 100%;
  margin-top: 20px;
}

.btn:hover {
  background-color: #333;
}


.result {
  margin-top: 30px;
  color:#333
}

.result h2 {
  font-size: 22px;
}

.result span {
  font-weight: bold;
  color: #333;
}

h1 {
  font-size: 22px;
  margin-bottom: 20px;
  color: #333;
}



</style>
