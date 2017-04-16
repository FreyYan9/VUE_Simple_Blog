<template>
    <div class='blog'>
        <div class="input">
            <div class='label'>
                <label class='show-err' for="input">请输入留言内容:</label>
                <transition name="fade">
                    <span v-if="show">( * 请输入留言内容 )</span>
                </transition>
            </div>
            <textarea @keyup.enter='publishContent' v-model="content" name="input" id="input" cols="30" rows="8" placeholder="请输入留言内容"></textarea>
            <!-- <span class="error">请输入浏览内容</span> -->
            <button @click="publishContent">发表留言</button>
        </div>
        <div class="todo">
            <h4>留言列表:</h4>
            <ul>
                <li v-for='item in resultData'>
                    <strong v-text="item.content"></strong>
                    <!-- <span v-text="item.createdAt | formatDate "></span> -->
                    <span>{{ item.createdAt | formatDate }}</span>
                </li>
                <li v-if="!resultData.length"> 暂无数据 </li>
            </ul>
        </div>
    </div>
</template>
<script>
export default {
    name: 'blog',
    data() {
        return {
            resultData: [],
            content: '',
            show: false
        }
    },
    watch: {
        content: function(val, oldVal) {
            console.log(oldVal);
        }
    },
    methods: {
        publishContent() {
            this.show = false
            if (!this.content) {
                this.show = true
                return
            }
            this.resultData.push({
                content: this.content,
                createdAt: Date.now()
            })
            this.content = ''
        }
    },
    filters: {
        formatDate: function(val) {
            return new Date(val).toLocaleString();
        }
    }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang='less'>
.blog {
    outline: none;
    width: 84%;
    padding: 1% 8%;
    .input {
        text-align: center;
        box-sizing: border-box;
        .label {
            text-align: left;
        }
        textarea {
            width: calc(100% - 8px);
            border: 1px solid #ccc;
            border-radius: 7px;
            margin-top: 10px;
            padding: 10px;
            outline: none;
            font-size:16px;
        }
        button {
            display: block;
            width: 100%;
            height: 40px;
            margin: 0 auto;
            font-size: 16px;
            border: 1px solid #ccc;
            background-color: #41b883;
            border-radius: 5px;
            margin-top: 5px;
            outline: none;
        }
        .fade-enter-active,
        .fade-leave-active {
            transition: opacity .5s;
        }
        .fade-enter,
        .fade-leave-active {
            opacity: 0
        }
        span {
            color: red;
        }
    }
    .todo {
        h4 {
            padding-left: 20px;
        }
        li {
            strong {
                font-size: 16px;
                margin-right: 5px;
            }
            span {
                font-size: 12px;
            }
        }
    }
}
</style>