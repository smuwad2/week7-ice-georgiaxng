<script>
import axios from 'axios';

export default {
    data() {
        return {
            mood: ["Happy", "Sad", "Neutral","Angry"],
            subject: "",
            entry: "",
            selectedMood: ''
        }
    },
    computed: {
        baseUrl() {
            if (window.location.hostname == 'localhost')
                return 'http://localhost:3000'
            else {
                const codespace_host = window.location.hostname.replace('5173', '3000')
                return `https://${codespace_host}`;
            }
        }
    },
    methods: {
        addPost() {
            axios.post(`${this.baseUrl}/addPost`, {

                    subject: this.subject,
                    entry: this.entry,
                    mood: this.selectedMood
                

            }).then(response => {
                console.log(response)
            }).catch(error=>{
                console.log(error)
            })
        }
    }

}
</script>

<template>
    <div class="table m-2">
        <h3>Add a New Blog Post</h3>

        Subject: <input type='text' size='30' v-model='subject' required>
        <br>

        Entry: <br>
        <textarea name='entry' cols='80' rows='5' v-model='entry' required></textarea>
        <br>

        Mood:
        <!-- TODO: Build a dropdown list here for selecting the mood -->
        <select v-model="selectedMood">
            <option v-for="m in mood">{{ m }}</option>
        </select>

        <br>

        <br>
        <button @click="addPost()">Submit New Post</button>

        <hr> Click <a><router-link to="/ViewPosts/">here</router-link></a> to return to Main Page

    </div>
</template>
