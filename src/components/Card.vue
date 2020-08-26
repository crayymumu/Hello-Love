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
import { content } from '@/assets/content'

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
      this.content = content
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
