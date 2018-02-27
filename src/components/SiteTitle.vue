<template>
    <div class="site-title">数字货币市场观察</div>
    
</template>

<script>
export default {
  props: {
    index: Number,
    news: Object
  }
};
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
    height: 65px;
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
