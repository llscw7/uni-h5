<template>
  <view class="container">
    <draggable v-model="items" item-key="id" :animation="200" :fallbackTolerance="3" :touchStartThreshold="5"
      :forceFallback="true" handle=".item" class="drag-list">
      <template #item="{ element }">
        <view class="item" @click="handleClick(element)">
          <view class="handle">≡</view>
          <text>{{ element.name }}</text>
        </view>
      </template>
    </draggable>
  </view>
</template>

<script setup>
import { ref } from 'vue'
import draggable from 'vuedraggable'

const handleClick = (item) => {
  console.log('Clicked item:', item)
  // 在这里处理点击事件，例如跳转到详情页等
  uni.webView.postMessage({
    data: {
      action: 'itemClicked',
      itemId: item.id
    }
  })
}

document.addEventListener('UniAppJSBridgeReady', function() {
        console.log(uni.webView,'lllll')
        // uni.webView.getEnv(function(res) {
        //   console.log('当前环境：' + JSON.stringify(res));
        // });
        // uni.webView.navigateTo(...)
      });

// document.addEventListener('UniAppJSBridgeReady', () => {
//   console.log(uni,'=====')
//   uni.webView.postMessage({ data: { msg: 'ready' } });
// });

const items = ref([
  { id: 1, name: '苹果' },
  { id: 2, name: '香蕉' },
  { id: 3, name: '橙子' },
  { id: 4, name: '西瓜' },
  { id: 5, name: '葡萄' },
  { id: 6, name: '芒果' },
  { id: 7, name: '菠萝' },
  { id: 8, name: '草莓' }
])
</script>

<style>
.container {
  padding: 20rpx;
}

.drag-list {
  display: flex;
  flex-direction: column;
  gap: 10rpx;
  touch-action: none;
  /* 禁用默认触摸行为 */
  overscroll-behavior-y: contain;
  /* 阻止滚动链 */
}

.item {
  display: flex;
  align-items: center;
  padding: 20rpx;
  background-color: #f5f5f5;
  border-radius: 8rpx;
  cursor: move;
  user-select: none;
}

.handle {
  margin-right: 20rpx;
  font-size: 24rpx;

}
</style>