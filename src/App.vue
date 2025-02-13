<template>
  <div class="happy-valentines">
    <div class="valentines-day-card">
      <div class="hearts">
        <div class="heartOne">
          <div class="left-side"></div>
          <div class="right-side"></div>
        </div>
        <div class="heartTwo">
          <div class="left-side"></div>
          <div class="right-side"></div>
        </div>
        <div class="heartThree">
          <div class="left-side"></div>
          <div class="right-side"></div>
        </div>
        <div class="heartFour">
          <div class="left-side"></div>
          <div class="right-side"></div>
        </div>
        <div class="heartFive">
          <div class="left-side"></div>
          <div class="right-side"></div>
        </div>
      </div>
      <div class="text" @click="playVideo">
        <span><br /></span>
      </div>
      <div class="video-container" v-if="showVideoOnClick">
        <video ref="videoPlayer" controls width="50%">
          <source :src="videoSrc" type="video/mp4" />
        </video>
      </div>
    </div>
    <p class="hover">- hover over the text -</p>
  </div>
</template>

<script>
import videoSrc from "../src/assets/video.mp4";

export default {
  data() {
    return {
      videoSrc,
      timerStarted: false,
      showVideoOnClick: false, // Biến này kiểm soát video
    };
  },
  methods: {
    playVideo() {
      this.showVideoOnClick = true; // Hiển thị video khi click vào chữ
      this.$nextTick(() => {
        const videoElement = this.$refs.videoPlayer;
        if (videoElement) {
          videoElement.play(); // Phát video sau khi click
        }
      });
    },
  },
};
</script>
<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Pacifico&display=swap");

body {
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #f35f7a;
}

.happy-valentines {
  display: flex;
  justify-content: center;
  align-items: center;
}

.valentines-day-card {
  position: relative;
  width: 400px;
  height: 300px;
  background-color: #ff8fa3;
  overflow: hidden;
  border: 10px solid white;
  border-radius: 10px;
  box-shadow: 0 0 100px rgba(0, 0, 0, 0.4);
  padding: 15%;
}

.valentines-day-card:before {
  content: "";
  position: absolute;
  background-color: #ffb3c1;
  width: 100px;
  height: 100px;
  border-radius: 50%;
  top: 140px;
  left: -25px;
  box-shadow: 60px 20px #ffb3c1, 130px 10px #ffb3c1, 190px 20px #ffb3c1,
    260px -5px #ffb3c1, 340px 20px #ffb3c1;
}

.valentines-day-card:after {
  content: "";
  position: absolute;
  background-color: #ffccd5;
  width: 100px;
  height: 100px;
  border-radius: 50%;
  top: 160px;
  left: -40px;
  box-shadow: 50px 20px #ffccd5, 120px 40px #ffccd5, 200px 15px #ffccd5,
    260px 30px #ffccd5, 330px 30px #ffccd5, 380px 10px #ffccd5;
}

.clouds {
  position: absolute;
  width: 100px;
  height: 100px;
  border-radius: 50%;
  background-color: #fff0f3;
  z-index: 5;
  top: 210px;
  left: -20px;
  box-shadow: 55px 30px #fff0f3, 125px 10px #fff0f3, 175px 20px #fff0f3,
    250px 10px #fff0f3, 320px 5px #fff0f3, 380px 10px #fff0f3;
}

.hearts {
  position: absolute;
  z-index: 2;
}

.heartOne {
  position: absolute;
  left: 100px;
  top: 250px;
  animation: up 4s linear forwards 1s;
}

.heartTwo {
  position: absolute;
  left: 270px;
  top: 230px;
  animation: up 5s linear forwards 1.8s;
}

.heartThree {
  position: absolute;
  left: 85px;
  top: 415px;
  animation: up 5s linear forwards 3s;
}

.heartFour {
  position: absolute;
  left: 320px;
  top: 380px;
  animation: upTwo 9s linear infinite 3.5s;
}

.heartFive {
  position: absolute;
  left: 150px;
  top: 400px;
  animation: upTwo 13s linear infinite 4.5s;
}

.right-side:before,
.right-side:after {
  position: absolute;
  content: "";
  transform-origin: left;
  animation: move 1s ease infinite;
}

.right-side:before {
  border-radius: 50% 50% 50% 0;
  width: 21px;
  height: 20px;
  background-color: #c9184a;
  left: -0.26px;
}

.right-side:after {
  height: 0;
  width: 0;
  border-bottom: 10px solid transparent;
  border-left: 15px solid #c9184a;
  top: 19px;
  left: -0.26px;
}

@keyframes move {
  0%,
  100% {
    transform: rotateY(0);
  }
  50% {
    transform: rotateY(-45deg);
  }
}

.left-side:before,
.left-side:after {
  position: absolute;
  content: "";
  transform-origin: right;
  animation: move 1s ease infinite;
}

.left-side:before {
  border-radius: 50% 50% 0 50%;
  width: 20px;
  height: 20px;
  left: -20.7px;
  background-color: #ff4d6d;
}

.left-side:after {
  height: 0;
  width: 0;
  left: -15px;
  border-bottom: 10px solid transparent;
  border-right: 15px solid #ff4d6d;
  top: 19px;
}

@keyframes up {
  0% {
    transform: translateY(0);
  }
  100% {
    transform: translateY(-200px);
  }
}

@keyframes upTwo {
  0% {
    transform: translateY(0);
  }
  100% {
    transform: translateY(-450px);
  }
}

.text {
  position: absolute;
  color: #800f2f;
  font-size: 30px;
  font-family: "Pacifico", cursive;
  line-height: 1;
  text-align: center;
  width: 380px;
  left: 10px;
  z-index: 3;
  top: 320px;
  animation: up 1s ease forwards;
  transition: 0.2s;
  cursor: pointer; /* Thêm hiệu ứng con trỏ khi hover */
}
.text span::before {
  content: "Happy Valentine's Đây bé Trúc yêu dấu của anh Lâm"; /* Nội dung mặc định */
}
.text:hover {
  color: #540101; /* Thay đổi màu khi hover */
  transform: scale(1.1); /* Phóng to phần tử khi hover */
  transition: 0.2s; /* Thêm hiệu ứng mượt mà */
}
.text:hover span::before {
  content: "Cám ơn một năm qua em đã luôn bên cạnh yêu thương và trân trọng anh, chúng ta sẽ bên cạnh nhau đến khi thế giới kết thúc em nhé yêu em Thanh Trúc mong em sẽ luôn khỏe mạnh để viết tiếp cuộc sống này cùng nhau.... <3 Anh yêu em"; /* Nội dung khi hover */
}
.hover {
  color: white;
  font-family: "Pacifico", cursive;
  text-align: center;
}

.video-container {
  display: block; /* Đảm bảo video hiển thị */
  z-index: 4;
  position: absolute;
  bottom: 20px;
  right: 10px; /* Di chuyển video sang bên phải */
  width: 50%; /* Điều chỉnh kích thước container */
  max-width: 400px; /* Giới hạn kích thước tối đa của container */
  height: auto;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
}

.video-container video {
  width: 100%; /* Đảm bảo video sử dụng toàn bộ chiều rộng của container */
  height: auto; /* Giữ tỷ lệ khung hình cho video */
}
</style>
