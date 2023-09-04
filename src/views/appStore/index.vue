<template>
  <div class="ma-content-block lg:flex justify-between p-4" ref="containerRef">
    <a-affix
      :offsetTop="18"
      :target="containerRef"
      class="w-2/12"
    >
      <div class="w-full h-full">
        <div class="font-bold leading-9 text-base">类型</div>
        <a-radio-group direction="vertical" v-model="form.type">
          <a-radio value="all">全部</a-radio>
          <a-radio value="1">完整应用</a-radio>
          <a-radio value="2">基础设施</a-radio>
          <a-radio value="3">前端组件</a-radio>
          <a-radio value="4">功能插件</a-radio>
        </a-radio-group>
        <a-divider />
        <div class="font-bold leading-9 text-base">货币</div>
        <a-radio-group direction="vertical"  v-model="form.currency">
          <a-radio value="all">全部</a-radio>
          <a-radio value="1">积分</a-radio>
          <a-radio value="2">人民币</a-radio>
        </a-radio-group>
      </div>
    </a-affix>
    <div class="w-10/12 ml-5 flex flex-col">
      <div class="lg:flex justify-between">
        <a-space>
          <a-button type="primary">会员信息</a-button>
          <a-button>本地应用</a-button>
          <a-button>上传安装</a-button>
        </a-space>
        <div class="w-6/12 flex">
          <a-input placeholder="搜索其实很简单" />
          <a-select class="w-full md:w-48 ml-2" placeholder="排序方式" allow-clear>
            <a-option value="price">按价格低到高</a-option>
            <a-option value="price">按价格高到低</a-option>
            <a-option value="timer">按更新时间</a-option>
            <a-option value="down">按下载量</a-option>
            <a-option value="fav">按收藏量</a-option>
            <a-option value="star">按点赞量</a-option>
          </a-select>
        </div>
      </div>
      <div class="applist-card block md:grid md:grid-cols-4 md:gap-4">
        <a-card class="border mt-3 rounded relative flex-col" hoverable :bordered="false">
          <div
            style="background-image: url(https://img2.baidu.com/it/u=4047488721,455163148&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500); background-size: cover;"
            class="app-image rounded-t"
          >
            <div class="obscure">
              <a-button shape="circle" class="circle-btn">
                <a-spin v-if="false" />
                <icon-thumb-up-fill class="text-3xl icon star" v-else />
              </a-button>
              <a-button shape="circle" class="circle-btn">
                <a-spin v-if="false" />
                <icon-star-fill class="text-3xl icon fav" v-else />
              </a-button>
              <a-button shape="circle" class="circle-btn"><icon-right class="text-3xl icon go" /></a-button>
            </div>
            <div class="tags">
              <a-space wrap>
                <a-tag color="#165dff">官方</a-tag>
                <a-tag color="#f53f3f">应用</a-tag>
              </a-space>
            </div>
          </div>
          <div class="app-info rounded-b flex-col">
            <div class="flex justify-between">
              社区论坛圈子小程序
              <!-- <a-tag color="green">免费</a-tag> -->
              <a-tag color="magenta">￥99</a-tag>
            </div>
            <div class="flex justify-between mt-2">
              <div>
                <icon-to-bottom /> 0
                <icon-star class="ml-2" /> 0
                <icon-thumb-up class="ml-2" /> 0
              </div>
              <a-dropdown @select="handleMore($event, 1)">
                <a-button size="mini" class="more"><icon-more-vertical /></a-button>
                <template #content>
                  <a-doption value="team"><icon-user-group class="mr-1" />团队介绍</a-doption>
                  <a-doption value="version"><icon-experiment class="mr-1" />版本记录</a-doption>
                </template>
              </a-dropdown>
            </div>
          </div>
        </a-card>
        <a-card class="border mt-3 rounded relative flex-col" hoverable :bordered="false">
          <div
            style="background-image: url(https://img2.baidu.com/it/u=4047488721,455163148&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500); background-size: cover;"
            class="app-image rounded-t"
          >
            <div class="obscure">
              <a-button shape="circle" class="circle-btn">
                <a-spin v-if="false" />
                <icon-thumb-up-fill class="text-3xl icon star" v-else />
              </a-button>
              <a-button shape="circle" class="circle-btn">
                <a-spin v-if="false" />
                <icon-star-fill class="text-3xl icon fav" v-else />
              </a-button>
              <a-button shape="circle" class="circle-btn"><icon-right class="text-3xl icon go" /></a-button>
            </div>
            <div class="tags">
              <a-space wrap>
                <a-tag color="#165dff">官方</a-tag>
                <a-tag color="#f53f3f">应用</a-tag>
              </a-space>
            </div>
          </div>
          <div class="app-info rounded-b flex-col">
            <div class="flex justify-between">
              会员签到
              <a-tag color="green">积分：50</a-tag>
              <!-- <a-tag color="magenta">￥99</a-tag> -->
            </div>
            <div class="flex justify-between mt-2">
              <div>
                <icon-to-bottom /> 0
                <icon-star class="ml-2" /> 0
                <icon-thumb-up class="ml-2" /> 0
              </div>
              <a-dropdown @select="handleMore($event, 1)">
                <a-button size="mini" class="more"><icon-more-vertical /></a-button>
                <template #content>
                  <a-doption value="team"><icon-user-group class="mr-1" />团队介绍</a-doption>
                  <a-doption value="version"><icon-experiment class="mr-1" />版本记录</a-doption>
                </template>
              </a-dropdown>
            </div>
          </div>
        </a-card>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const containerRef = ref()

const form = ref({
  type: 'all', currency: 'all'
})
</script>

<style scope lang="less">
.applist-card .arco-card-body {
  padding: 0; background-color: none; overflow: hidden;
}

.app-info {
  height: 80px; background:var(--color-bg-white); padding: 10px;
  .more {
    padding: 0 5px !important;
  }
}

.app-image {
  width: 100%; height: 220px; background-size: cover; color: #fff;
  position: relative;  overflow: hidden;
  .obscure {
    background: rgba(#fff, 0.2); cursor: pointer;
    backdrop-filter: blur(2px); position: absolute; width: 100%; height: 100%; display: none; z-index: 2;
    .circle-btn {
      width: 60px; height: 60px; background: #fff; margin-top: 10px;
      .icon {
        color: #000;
      }
    }
    .circle-btn:hover .star {
      color: #f53f3f;
    }
    .circle-btn:hover .fav {
      color: #ffb400;
    }
    .circle-btn:hover .go {
      color: #165dff;
    }
  }
  .tags {
    position: absolute; z-index: 3; margin-top: 8px; width: 100%; padding: 0 10px;
  }
}

.app-image:hover {
  .obscure { display: flex; justify-content: space-around; align-items: center; }
}
</style>