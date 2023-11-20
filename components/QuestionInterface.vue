<template>
    <h1>
        Ask a question:
    </h1>
    <input type="text" v-model="userQuestion" />
    <button @click="askModel">
        Run
    </button>
</template>

<script setup>
const userQuestion = ref("Which is the most prescribed medication?")
const request = {
    method: "POST", // *GET, POST, PUT, DELETE, etc.
    mode: "cors", // no-cors, *cors, same-origin
    cache: "no-cache", // *default, no-cache, reload, force-cache, only-if-cached
    credentials: "same-origin", // include, *same-origin, omit
    headers: {
        "Content-Type": "application/json",
        "Authorization": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6InRucnVnb3F5bHN1eXp5enBqY21iIiwicm9sZSI6ImFub24iLCJpYXQiOjE3MDAwOTE3MDgsImV4cCI6MjAxNTY2NzcwOH0.JXv1KPFTPsFUew--Wk_jZhj20Qu4tZldLlWRUjKhxKc"
        // 'Content-Type': 'application/x-www-form-urlencoded',
    },
    redirect: "follow", // manual, *follow, error
    referrerPolicy: "no-referrer", // no-referrer, *no-referrer-when-downgrade, origin, origin-when-cross-origin, same-origin, strict-origin, strict-origin-when-cross-origin, unsafe-url
    body: JSON.stringify({ userQuestion: userQuestion.value }), // body data type must match "Content-Type" header
}
const askModel = async () => {
    userQuestion.value = userQuestion.value + " " + userQuestion.value
    const users = await $fetch('https://tnrugoqylsuyzyzpjcmb.supabase.co/functions/v1/browser_call', request).catch((error) => error)
}
</script>