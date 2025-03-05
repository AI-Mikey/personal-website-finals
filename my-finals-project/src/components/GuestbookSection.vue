<template>
  <section id="guestbook" class="section">
    <h2 class="section-title">Guestbook</h2>
    
    <div class="guestbook-form">
      <h3>Leave a Message</h3>
      <form @submit.prevent="submitComment">
        <div class="form-group">
          <label for="name">Name</label>
          <input 
            type="text" 
            id="name" 
            v-model="newComment.name" 
            required 
            placeholder="Your name"
          />
        </div>
        <div class="form-group">
          <label for="email">Email</label>
          <input 
            type="email" 
            id="email" 
            v-model="newComment.email" 
            required 
            placeholder="Your email"
          />
        </div>
        <div class="form-group">
          <label for="message">Message</label>
          <textarea 
            id="message" 
            v-model="newComment.message" 
            required 
            placeholder="Your message"
            rows="4"
          ></textarea>
        </div>
        <button type="submit" class="btn" :disabled="isSubmitting">
          {{ isSubmitting ? 'Submitting...' : 'Submit' }}
        </button>
      </form>
    </div>
    
    <div class="comments-section">
      <h3>Messages ({{ comments.length }})</h3>
      <div v-if="isLoading" class="loading">
        <p>Loading comments...</p>
      </div>
      <div v-else-if="comments.length === 0" class="no-comments">
        <p>No messages yet. Be the first to leave a message!</p>
      </div>
      <div v-else class="comments-list">
        <div v-for="comment in comments" :key="comment.id" class="comment-card">
          <div class="comment-header">
            <h4>{{ comment.name }}</h4>
            <span class="comment-date">{{ formatDate(comment.created_at) }}</span>
          </div>
          <p class="comment-message">{{ comment.message }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { supabase } from '../lib/supabaseClient';

const comments = ref([]);
const isLoading = ref(true);
const isSubmitting = ref(false);
const newComment = ref({
  name: '',
  email: '',
  message: ''
});

// Fetch comments from Supabase
const fetchComments = async () => {
  try {
    isLoading.value = true;
    const { data, error } = await supabase
      .from('comments')
      .select('*')
      .order('created_at', { ascending: false });
    
    if (error) throw error;
    
    comments.value = data || [];
  } catch (error) {
    console.error('Error fetching comments:', error);
    alert('Failed to load comments. Please try again later.');
  } finally {
    isLoading.value = false;
  }
};

// Submit a new comment
const submitComment = async () => {
  try {
    isSubmitting.value = true;
    
    const { data, error } = await supabase
      .from('comments')
      .insert([
        {
          name: newComment.value.name,
          email: newComment.value.email,
          message: newComment.value.message
        }
      ]);
    
    if (error) throw error;
    
    // Reset form
    newComment.value = {
      name: '',
      email: '',
      message: ''
    };
    
    // Refresh comments
    await fetchComments();
    
    alert('Your message has been submitted successfully!');
  } catch (error) {
    console.error('Error submitting comment:', error);
    alert('Failed to submit your message. Please try again later.');
  } finally {
    isSubmitting.value = false;
  }
};

// Format date
const formatDate = (dateString) => {
  const date = new Date(dateString);
  return date.toLocaleDateString('en-US', {
    year: 'numeric',
    month: 'short',
    day: 'numeric',
    hour: '2-digit',
    minute: '2-digit'
  });
};

// Fetch comments on component mount
onMounted(() => {
  fetchComments();
});
</script>

<style scoped>
.section {
  background: url('https://github.com/AI-Mikey/personal-website-finals/raw/main/my-finals-project/img/wallpapersden.com_new-warframe-2023_1920x960%20(3).jpg') no-repeat center center;
  background-size: cover;
  padding: 50px 20px; /* Adjust padding as needed */
  color: white; /* Change text color for contrast */
}
.section-title {
  margin-bottom: 1rem;
  color: white;
}

.guestbook-form {
  margin-bottom: 2rem;
  background-color: rgba(255, 255, 255, 0);
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0);
}

.guestbook-form h3 {
  margin-bottom: 1rem;
  color: white;
}

.form-group {
  margin-bottom: 1rem;
}

.form-group label {
  display: block;
  margin-bottom: 0.5rem;
  font-weight: 500;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid var(--border);
  border-radius: 5px;
  font-family: inherit;
  font-size: 1rem;
  transition: border-color 0.3s ease;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: var(--primary);
}

.comments-section h3 {
  margin-bottom: 1rem;
  color: white;
}

.loading, .no-comments {
  text-align: center;
  padding: 2rem;
  background-color: rgba(255, 255, 255, 0.06);
  border-radius: 8px;
}

.comments-list {
  display: grid;
  gap: 1rem;
}

.comment-card {
  background-color: rgba(255, 255, 255, 0.8);
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.06);
}

.comment-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.5rem;
}

.comment-header h4 {
  margin: 0;
  color: white;
}

.comment-date {
  font-size: 0.8rem;
  color: var(--light-text);
}

.comment-message {
  margin: 0;
  white-space: pre-line;
}
</style>