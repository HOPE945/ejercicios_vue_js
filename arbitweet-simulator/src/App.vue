<template>
  <Menu :openCloseForm="openCloseForm" :showForm="showForm" />
  <TweetForm
    :showForm="showForm"
    :openCloseForm="openCloseForm"
    :reloadTweets="reloadTweets"
  />
  <TweetList :tweets="tweets" :reloadTweets="reloadTweets" />
</template>

<script>
import { ref } from "vue";
import Menu from "./components/Menu";
import TweetForm from "./components/TweetForm";
import TweetList from "./components/TweetList";
import useFormTweet from "./hooks/useFormTweet";
import { getTweetApi } from "./api/tweet";

export default {
  name: "App",
  components: {
    Menu,
    TweetForm,
    TweetList,
  },
  setup() {
    let tweets = ref(getTweetApi().reverse());

    const reloadTweets = () => {
      tweets.value = getTweetApi().reverse();
    };

    return {
      ...useFormTweet(),
      tweets,
      reloadTweets,
    };
  },
};
</script>

<style lang="scss"></style>
