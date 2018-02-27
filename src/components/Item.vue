<template>
  <b-list-group-item>
    <div class="site-name">{{ news.site_name }}</div>
    <div class="news-info">
      <span class="new-title">
    <a :href= "news.link" target="_blank">{{ news.title }}</a></span>
      <span class="news-date">{{ news.date }}</span></div>
  </b-list-group-item>
</template>

<script>
export default {
  props: {
    index: Number,
    news: Object
  }
}
</script>

<style>
.item {
  height: 100%;
  line-height: 50px;
  padding-left: 20px;
  border-bottom: 1px solid #eee;
}
.site-name {
    float: left;
    background:rgba(0,0,0,0.7);
    color:  white;
    height: 65px;
    min-width:  99px;
    line-height:  65px;
}

.news-info {
    float:  left;
    margin-left:  5px;
    color: black;
    background: #fffbfb;
    width: 80%;
    min-height: 65px;
}

span.new-title {
    color: black;
    font-size: 20px;
    float:  left;
    width: 100%;
    text-align:  left;
    text-indent: 5px;
    padding: 5px;
}

span.news-date {
    float:  left;
    text-align:  left;
    text-indent: 5px;
    padding-left: 5px;}
</style>
