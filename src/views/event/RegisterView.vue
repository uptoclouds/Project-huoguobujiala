<template>
  <div class="comment-container">
    <p>Leave a comment for the athletes</p>
    <input v-model="newCommentText" placeholder="Type a comment" />
    <button @click="addComment" :style="{ backgroundColor: '#4CAF50', color: 'white' }"> Add Comment </button>
    <div v-for="comment in comments" :key="comment.id" class="comment-box">
      {{ comment.text }}
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, defineProps, computed } from 'vue';
import { useCommentsStore } from '@/stores/message';
import type { Comment } from '@/type'; // 确保路径正确

const props = defineProps<{
  event: { countryName: string; id: string };
}>();
const store = useCommentsStore();
const comments = computed(() => store.getAllComments().filter(comment => comment.eventId === props.event.id));
const newCommentText = ref('');

const addComment = () => {
  if (newCommentText.value.trim()) {
    const newComment: Comment = {
      id: Date.now().toString(),
      text: newCommentText.value,
      eventId: props.event.id
    };
    store.addComment(newComment);
    newCommentText.value = ''; // 清空输入框
  }
};
</script>

<style scoped>
.comment-container {
  max-width: 600px; 
  margin: 20px auto;
  padding: 20px; 
  background-color: #f9f9f9; 
  border-radius: 8px; 
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

input {
  display: block;
  width: 100%;
  padding: 10px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  display: block;
  width: 100%;
  padding: 10px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #45a049; 
}

.comment-box {
  margin-top: 15px;
  padding: 10px;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 4px;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
}
</style>