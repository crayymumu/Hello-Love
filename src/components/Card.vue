<template>
  <div class="card-content">
    <div
      v-for="(item, index) in content"
      :key="index"
      class="card-item"
    >
      <template v-if="currentPage === index">
        <wired-card elevation="5">
          <vue-typed-js
            :strings="Array.isArray(item)? item : [item]"
            :show-cursor="false"
            :type-speed="50"
            :back-delay="100"
            :back-speed="25"
          >
            <p class="typing" />
          </vue-typed-js>
        </wired-card>
      </template>
    </div>
    <div class="card-pagination">
      <div
        v-if="currentPage !== 0"
        class="card-btn card-prev"
        @click="prev"
      >
        <wired-button elevation="3">
          上一页
        </wired-button>
      </div>
      <div
        v-if="currentPage !== content.length - 1"
        class="card-btn card-next"
        @click="next"
      >
        <wired-button elevation="3">
          下一页
        </wired-button>
      </div>
    </div>
  </div>
</template>

<script>
import WiredButton from 'wired-button'
import WiredCard from 'wired-card'

export default {
  name: 'Card',
  components: {
    WiredButton,
    WiredCard
  },
  data() {
    return {
      currentPage: 0,
      content: []
    }
  },
  created() {
    this.initContent()
  },
  methods: {
    initContent() {
      this.content = [
        ['人和人之间想要保持长久舒适的关系，靠的是共性和吸引，而不是压迫，捆绑。奉承和一味的付出，以及道德式的自我感动。', '对不起，等你疏远了我，我才明白。'],
        '我真不知怎么才能和你亲近起来，你好像是一个可望而不可及的目标，我琢磨不透，追也追不上，就坐下哭了起来。 你要是喜欢别人我会哭，但是还是喜欢你。',
        '实在无法相见，也无话可说时，就去他的朋友圈发一会儿呆，就去他的微博发一会儿呆，仿佛走进了此人的房间。他不在，我独自坐在窗边吹了会儿风，对着他遗留下的数据，哪怕是一粒尘埃，也凝视良久。<br\>这样一想，我们每个人的主页，都承载过多少次这样的凝视啊。当代人类的深情，最后只能以这种形式保存。',
        '我渴望见你一面<br\>' +
        '但我不会再开口要求要见你<br\>' +
        '这不是因为骄傲<br\>' +
        '你知道我在你面前毫无骄傲可言<br\>' +
        '而是因为<br\>' +
        '唯有你想见到我的时候<br\>' +
        '我们见面才有意义',
        ['世界上最廉价的东西是什么？', '大概就是付出吧', '一贫如洗的真心，一事无成的温柔。'],
        '我希望自己能够有足够的运气与足够的勇气去见到命运里更多不同的风。<br\>' +
        '也期待在未来的日子里，能够被这些涌动的气流雕刻成不一样的山川与河流。',
        '时间总是把对你最好的人留在最后<br\>' +
        '毕竟喜欢就像一阵风而爱是细水长流'
      ]
    },
    /**
     * 下一页
     */
    prev() {
      this.currentPage--
    },
    /**
     * 下一页
     */
    next() {
      this.currentPage++
    }
  }
}
</script>

<style lang="scss">
.card-content {
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  .card-item {
    width: 90%;
    font-size: 2rem;
    line-height: 2.5rem;
    background-color: rgba(255, 255, 255, 0.8);

    .wired-rendered,
    .typed-element {
      height: 60vh;
      display: flex;
      align-items: center;
      padding: 20px;
    }
  }

  .card-pagination {
    width: 90%;
    display: flex;
    margin-top: 3rem;
    padding: 1rem;
    justify-content: space-around;
  }
}
</style>
