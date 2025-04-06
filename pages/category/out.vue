<template>
    <div class="page">
      <div class="main">
        <draggable v-model="categories" item-key="id" :animation="200" :fallbackTolerance="3" :touchStartThreshold="5"
          :forceFallback="true" handle=".drag-list-item" class="drag-list">
          <template #item="{ element }">
            <div class="card drag-list-item"  @click="handleClick(element)">
              <div class="card-item">
                <div class="left">
                  <uni-icons fontFamily="iconfont-class" :size="18" color="rgb(99, 102, 241)">{{class_icons[element.fontIcon]}}</uni-icons>
                  <text class="card-label">{{ element.name }}</text>
                </div>
                
                <div class="right">
                  <uni-icons type="compose" size="20" color="#999999"></uni-icons>
                  <uni-icons type="bars" size="20" color="#999999"></uni-icons>
                </div>
              </div>
            </div>
          </template>
        </draggable>
        

        <div class="card">
          <div class="card-item">
            <text class="card-label">指定账户</text>
            <div class="right">
              <text class="placeholder-text">点此选择 (可不选)</text>
              <uni-icons type="right" size="16" color="#d1d5db" />
            </div>
          </div>

        </div>

        <div class="card">
          <div class="card-item">
            <text class="card-label">指定账本</text>
            <div class="right">
              <text class="placeholder-text">点此选择 (可不选)</text>
              <uni-icons type="right" size="16" color="#d1d5db" />
            </div>
          </div>
        </div>

        <div class="card">
          <div class="card-item">
            <text class="card-label">包含图片附件或链接</text>
            <switch class="switch" color="rgb(99, 102, 241)" :checked="false" />
          </div>
        </div>
      </div>

      <div class="bottom-bar">
        <div class="option-button">
          <text class="button-text">保存</text>
        </div>
      </div>
    </div>
</template>

<script lang="ts" setup>
import { ref } from 'vue'
import other_icons from '@/common/icon/other-icon'
import class_icons from '@/common/icon/class-icon'
import { categories_out } from '@/common/icon/categories'
import draggable from 'vuedraggable'

const categories = ref(categories_out)

const handleClick = (item) => {
  console.log('Clicked item:', item)
}

const goBack = () => {
  uni.navigateBack();
};
</script>

<style lang="less" scoped>
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

.page {
  // background-color: #f5f5f5;
  min-height: 100%;
  padding-bottom: 200rpx;
  box-sizing: border-box;
}

.main {
  padding: 32rpx;
}

.card {
  position: relative;
  background-color: #ffffff;
  border-radius: 30rpx;
  margin-bottom: 20rpx;
  box-shadow: 0 4rpx 20rpx rgba(0, 0, 0, 0.05);
}

.card-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 32rpx;
}

.left {
  display: flex;
  align-items: center;
  gap: 20rpx;
}

.border-bottom {
  border-bottom: 1px solid #f0f0f0;
}

.card-label {
  font-size: 14px;
  color: #333333;
}

.right {
  display: flex;
  align-items: center;
  gap: 20rpx;
}

.value-text {
  font-size: 14px;
  color: #666666;
  margin-right: 16rpx;
}

.placeholder-text {
  font-size: 14px;
  color: #999999;
  margin-right: 16rpx;
}

.switch {
  transform: scale(0.8);
}

.bottom-bar {
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0rpx;
  padding: 32rpx;
  background-color: #ffffff;
  border-top: 1px solid #f0f0f0;
}

.option-button {
  width: 100%;
  height: 88rpx;
  background-color: rgb(99, 102, 241);
  border-radius: 88rpx;
  color: #ffffff;
  font-size: 14px;
  font-weight: 500;
  display: flex;
  align-items: center;
  justify-content: center;
  border: none;
  margin-bottom: 20rpx;
}
</style>