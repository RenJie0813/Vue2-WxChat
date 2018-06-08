<template>
  <div id="wechat">
    <search></search>
    
    <ul class="wechat-list" v-show="!getHeaderStatus">
      <!--props传递消息对象 baseMsgObj -->
      <chat-item v-on:delete="deleteOne" v-for="baseMsgObj in getChatList" :item="baseMsgObj"
        class="list-row line-bottom" :key="baseMsgObj.chatId"></chat-item>
    </ul>
  </div>
</template>

<script>
  import chatItem from '../components/chatItem.vue'
  import search from '../components/search.vue'
  import {
    mapGetters
  } from 'vuex'

  export default {
    data() {
      return {
      }
    },
    computed: {
      ...mapGetters(['getHeaderStatus','getChatList'])
    },
    methods: {
      deleteOne(data) {
        this.$store.dispatch("delChatItem",data.chatId);
      }
    },
    mounted() {

    },
    created() {
    },
    components: {
      chatItem,
      search
    },
    // beforeRouteLeave: function (to, from, next) {
    //   window.c = document.body.scrollTop;
    //   next();
    // },
    // beforeRouteEnter: function (to, from, next) {
    //   next();
    //   setTimeout(function () {
    //     document.body.scrollTop = window.c;
    //   }, 0)
    // }
  }
</script>

<style>
  @import "../../static/css/chat.css";
</style>
