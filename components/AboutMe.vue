<template>
  <article-card style="margin-top: 100px">
    <div slot="card-content">
      <div class="author">
        <img
          class="author-head"
          :src="$page.frontmatter.head || 'https://user-gold-cdn.xitu.io/2019/5/15/16aba753c5c2e3b5?w=406&h=392&f=gif&s=155219'"
          alt="headimg"
        >
        <!-- <div class="card-title" slot="card-title">About Me</div> -->
        <div class="author-info">
          <div class="info-item">
            <i class="iconfont iconwenzhang"></i>
            <CountUp startNum="0" :endNum="postsNum" times="10" speed="50" />
          </div>
          <!-- <div class="info-item">
            <i class="iconfont iconwenjianjia"></i>
            <CountUp startNum="0" :endNum="classNum" times="10" speed="50" />
          </div> -->
          <div class="info-item">
            <i class="iconfont icontag"></i>
            <CountUp startNum="0" :endNum="tagsNum" times="10" speed="50" />
          </div>
        </div>
        <div v-if="$page.frontmatter.introduction" class="introduction">
          {{ $page.frontmatter.introduction }}
        </div>
      </div>
    </div>
  </article-card>
</template>

<script>
import ArticleCard from "./ArticleCard.vue";
import CountUp from './CountUp';
export default {
  // props: {
  //   postsNum: {
  //     type: Number,
  //     default: 0
  //   },
  //   classNum: {
  //     type: Number,
  //     default: 0
  //   },
  //   tagsNum: {
  //     type: Number,
  //     default: 0
  //   }
  // },
  data () {
    return {
      postsNum: 0,
      tagsNum: 0
    }
  },
  components: { ArticleCard , CountUp },
  mounted() {
    setTimeout(() => {
      this.postsNum = sessionStorage.getItem('postsNum')
      this.tagsNum = sessionStorage.getItem('tagsNum')
    }, 0);
  },
  computed: {
    options () {
      return {
        useEasing: true,
        useGrouping: true,
        separator: '',
        decimal: '.',
        decimalPlaces: '',
        prefix: '',
        suffix: ''
      }
    }
  }
};
</script>

<style lang="stylus" scoped>
.author {
  .author-head {
    width 192px
    height 192px
    transition: 0.5s;
    display: table;
    margin: -120px auto 30px;
    padding: 5px;
    border: 1px solid #e0e0e0;
    border-radius: 50%;
    background-color: #fff;

    &:hover {
      transform: rotate(360deg);
    }
  }
}

.introduction {
  text-align: center;
  margin-top: 15px;
}

.author-info {
  cursor pointer
  display flex
  .info-item {
    &:nth-child(1) {
      border 0
    }
    border-left 1px dashed #e0e0e0
    text-align center
    flex 1
    display flex
    flex-direction column
    justify-content center
    i {
      font-size 20px
    }
    span {
      font-size 10px
      justify-content center
    }
  }
}

.atc-title {
  border-left: 5px solid red;
  padding-left: 5px;
}
</style>