<template>
  <div class="ctr">
    <questions
      v-if="questionsAnswered < questions.length"
      :questions="questions"
      :questionsAnswered="questionsAnswered"
      @question-answered="questionAnswered"
    ></questions>
    <result v-else :results="results" :totalCorrect="totalCorrect"></result>
    <button
      type="button"
      class="reset-btn"
      @click.prevent="reset"
      v-if="this.questionsAnswered === questions.length"
    >
      Reset
    </button>
  </div>
</template>

<script>
import Questions from "./components/Questions.vue";
import Result from "./components/Result.vue";
export default {
  name: "App",
  components: {
    Questions,
    Result,
  },
  data() {
    return {
      questionsAnswered: 0,
      totalCorrect: 0,
      questions: [
        {
          q: "What is JavaScript primarily used for?",
          answers: [
            {
              text: "Styling web pages",
              is_correct: false,
            },
            {
              text: "Creating interactive web applications",
              is_correct: true,
            },
            {
              text: "Sending emails",
              is_correct: false,
            },
            {
              text: "Editing images",
              is_correct: false,
            },
          ],
        },
        {
          q: "What is the correct way to declare a variable in JavaScript?",
          answers: [
            {
              text: "variable myVar = 5;",
              is_correct: false,
            },
            {
              text: "var myVar = 5;",
              is_correct: true,
            },
            {
              text: "myVar = 5;",
              is_correct: false,
            },
            {
              text: "let myVar = 5;",
              is_correct: false,
            },
          ],
        },
        {
          q: "What does DOM stand for in JavaScript?",
          answers: [
            {
              text: "Document Object Model",
              is_correct: true,
            },
            {
              text: "Dynamic Object Model",
              is_correct: false,
            },
            {
              text: "Data Oriented Model",
              is_correct: false,
            },
            {
              text: "Desktop Oriented Model",
              is_correct: false,
            },
          ],
        },
        {
          q: "How can you comment a single line in JavaScript?",
          answers: [
            {
              text: "// This is a comment",
              is_correct: true,
            },
            {
              text: "/* This is a comment */",
              is_correct: false,
            },
            {
              text: "# This is a comment",
              is_correct: false,
            },
            {
              text: "' This is a comment",
              is_correct: false,
            },
          ],
        },
        {
          q: "What is an array in JavaScript?",
          answers: [
            {
              text: "A type of loop",
              is_correct: false,
            },
            {
              text: "A built-in function",
              is_correct: false,
            },
            {
              text: "A collection of values",
              is_correct: true,
            },
            {
              text: "A type of variable",
              is_correct: false,
            },
          ],
        },
        {
          q: "Which keyword is used to declare a function in JavaScript?",
          answers: [
            {
              text: "method",
              is_correct: false,
            },
            {
              text: "function",
              is_correct: true,
            },
            {
              text: "procedure",
              is_correct: false,
            },
            {
              text: "class",
              is_correct: false,
            },
          ],
        },
        {
          q: "What is the result of 5 + '5' in JavaScript?",
          answers: [
            {
              text: "55",
              is_correct: true,
            },
            {
              text: "10",
              is_correct: false,
            },
            {
              text: "Error",
              is_correct: false,
            },
            {
              text: "5",
              is_correct: false,
            },
          ],
        },
        {
          q: "What does the 'typeof' operator in JavaScript return for a function?",
          answers: [
            {
              text: "Function",
              is_correct: true,
            },
            {
              text: "Object",
              is_correct: false,
            },
            {
              text: "Method",
              is_correct: false,
            },
            {
              text: "Type",
              is_correct: false,
            },
          ],
        },
        {
          q: "What is a closure in JavaScript?",
          answers: [
            {
              text: "A way to lock variables",
              is_correct: false,
            },
            {
              text: "A method to call functions",
              is_correct: false,
            },
            {
              text: "A function that has access to its parent's scope",
              is_correct: true,
            },
            {
              text: "A built-in JavaScript class",
              is_correct: false,
            },
          ],
        },
        {
          q: "Which operator is used to combine two or more strings in JavaScript?",
          answers: [
            {
              text: "+",
              is_correct: true,
            },
            {
              text: "-",
              is_correct: false,
            },
            {
              text: "&",
              is_correct: false,
            },
            {
              text: "|",
              is_correct: false,
            },
          ],
        },
      ],
      results: [
        {
          min: 0,
          max: 4,
          title: "Try again!",
          desc: "Do a little more studying and you may succeed!",
        },
        {
          min: 5,
          max: 8,
          title: "Wow, you're good!",
          desc: "Keep up the good work!",
        },
        {
          min: 9,
          max: 10,
          title: "You're a genius!",
          desc: "Studying has definitely paid off for you!",
        },
      ],
    };
  },
  methods: {
    questionAnswered(is_correct) {
      if (is_correct) {
        this.totalCorrect++;
      }
      this.questionsAnswered++;
    },
    reset() {
      this.questionsAnswered = 0;
      this.totalCorrect = 0;
    },
  },
};
</script>

<style></style>
