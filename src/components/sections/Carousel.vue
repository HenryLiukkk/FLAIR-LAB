<script>
import { Swiper, SwiperSlide } from 'swiper/vue';
import { Navigation, Pagination, Autoplay } from 'swiper/modules';
import 'swiper/css/bundle';

export default {
  components: {
    Swiper,
    SwiperSlide,
    Navigation,
    Pagination,
    Autoplay,
  },
  data() {
    return {
      modules: [
        Navigation,
        Pagination,
        Autoplay,
      ],
      // 选择要轮播的 GIF 图片
      image_paths: [
        "./carousel/1.gif",
        "./carousel/2.gif",
        "./carousel/3.gif",
        "./carousel/4.gif",
        "./carousel/5.gif",
        "./carousel/7.gif",
        "./carousel/8.gif",
        "./carousel/9.gif",
      ],
    }
  }
}
</script>

<template>
  <el-row justify="center">
    <el-col :span="24">
      <!-- 设置轮播图：循环播放、首张图序号、响应式、导航和分页、自动播放 -->
      <swiper
        :loop="true"
        :slidesPerView="1"
        :breakpoints="{
          600: {
            slidesPerView: 2,
          },
          800: {
            slidesPerView: 3,
          },
        }"
        :modules="modules"
        :navigation="{ 
          hideOnClick:true,
        }"
        :pagination="{ 
          hideOnClick:true,
          clickable:true, 
          type:'bullets' 
        }"
        :autoplay="{ 
          delay:5000,
          disableOnInteraction:false,
          pauseOnMouseEnter:true,
        }"
      >
        <swiper-slide v-for="(path, index) in image_paths" :key="index">
          <el-image :src="path" class="carousel-image" />
        </swiper-slide>
      </swiper>
    </el-col>
  </el-row>
</template>

<style>
/* 设置 Swiper 风格 */
.swiper {
  --swiper-theme-color: white;
}

/* 定义 carousel-image 类的样式 */
.carousel-image {
  width: 800px;
  height: 450px;
  object-fit: cover; /* 确保图片保持比例并填充容器 */
}
</style>
