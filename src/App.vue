<template>
  
</template>

<script>
export default {
  data(){
    return {
      current_question: 0,
      questions: [
        {
          title: "What is PHP ?",
          correct_answer:1,
          answers: [
            "HyperText PreProcessor",
            "Personal HomePage",
            "Private Hypertext Processor",
            "All the above are incorrect",
          ],
        },
      ]
    };
  }
}
</script>