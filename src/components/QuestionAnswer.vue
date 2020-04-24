<template>
    <div class="container">
        <input class="search" type="text" v-model="value" placeholder="search">
        <ul class="questions">  
            <li class="question-wrapper" v-for="(q, index) in localData" :key="index"> 
                    <p class="question">{{ q.question }}</p>
                    <p class="answer">{{ q.answer }}</p>
                    <a class="link" :href="q.link" v-if="q.link" target="_blank">{{ q.linkText }}</a>
                    <div v-if="q.suggestions" class="suggestions">
                        <li v-for="(item, index) in q.suggestions" :key="index"> <a class="link" :href="item.link">{{ item.linkText }}</a></li>
                    </div>
            </li> 
        </ul>
    </div>
</template>

<script>
export default {
    props: ['qaData'],
    data() {
        return {
            value: ''
        }
    },
    computed: {
        localData() {
            return this.qaData.filter((item) => item.question.toLowerCase().match(this.value.toLowerCase()));
        }
    }
}
</script>

<style scoped>

    .search {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        height: 40px;
        width: 500px;
        border-radius: 20px;
        border: 1px solid #C1C3E4;
        box-shadow: none;
        outline: none;
        padding-left: 14px;
        font-size: 16px;
    }

    .questions {
        list-style-type: none;
        padding: 0;
    }

    .answer {
        line-height: 30px;
    }

    .question-wrapper {
        margin: 20px 0;
        color: #3e437c;
        font-size: 16px;
        list-style-type: none;
        background: white;
        padding: 20px;
        border-radius: 10px;
        position: relative;
        max-width: 650px;
    }

    p {
        margin-top: 0;
    }

    p:last-child {
        margin-bottom: 0;
    }

    .question {
        font-weight: 600;
    }

    .link {
        color: #2fa178;
        font-weight: bold;
    }

    .suggestions li:not(:last-child){
            margin-bottom: 10px;
    }

    @media (max-width: 500px) {
        .container {
            width: 100%;
        }

        .search {
            width: 100%;
        }

        .questions {
            width: 100%;
        }
        .question-wrapper {
            min-width: auto;
        }
    }

</style>