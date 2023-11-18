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
const userQuestion = ref("Here")
const request = {
    method: "POST", // *GET, POST, PUT, DELETE, etc.
    mode: "cors", // no-cors, *cors, same-origin
    cache: "no-cache", // *default, no-cache, reload, force-cache, only-if-cached
    credentials: "same-origin", // include, *same-origin, omit
    headers: {
        "Content-Type": "application/json",
        // 'Content-Type': 'application/x-www-form-urlencoded',
    },
    redirect: "follow", // manual, *follow, error
    referrerPolicy: "no-referrer", // no-referrer, *no-referrer-when-downgrade, origin, origin-when-cross-origin, same-origin, strict-origin, strict-origin-when-cross-origin, unsafe-url
    body: JSON.stringify({ userQuestion: userQuestion.value }), // body data type must match "Content-Type" header
}
const askModel = async () => {
    userQuestion.value = userQuestion.value + " " + userQuestion.value
    const users = await $fetch('/api/nl2sql_endpoint', request).catch((error) => error)
}
</script>