<script setup>
import { ref } from 'vue'

const isMenuClose = ref(true)

const toggleMenu = () => {
  isMenuClose.value = !isMenuClose.value

  if (isMenuClose.value) {
    document
      .getElementById('globalnav-anim-menutrigger-bread-bottom-close')
      .beginElement()
    document
      .getElementById('globalnav-anim-menutrigger-bread-top-close')
      .beginElement()
  } else {
    document
      .getElementById('globalnav-anim-menutrigger-bread-bottom-open')
      .beginElement()
    document
      .getElementById('globalnav-anim-menutrigger-bread-top-open')
      .beginElement()
  }
}

const navItems = [
  { text: '지역', link: '#' },
  { text: '여행코스', link: '#' },
]
</script>

<template>
  <div id="global-header">
    <nav id="global-nav">
      <div id="global-nav-content">
        <!--1-->
        <ul class="ul-item">
          <!--로고-->
          <li>
            <RouterLink to="/" class="icon-box">
              <img alt="Trip logo" src="@/assets/23532_color.svg" width="30" />
            </RouterLink>
          </li>
          <!--메뉴-->
          <li class="nav-item">
            <div
              class="nav-items"
              v-for="(item, index) in navItems"
              :key="index"
            >
              <div>{{ item.text }}</div>
              <v-icon icon="mdi-chevron-right"></v-icon>
            </div>
          </li>
          <!--돋보기-->
          <li>
            <button class="icon-box">
              <v-icon icon="mdi-magnify" size="small" color="black" />
            </button>
          </li>
          <!--즐겨찾기-->
          <li>
            <button class="icon-box">
              <v-icon icon="mdi-star-outline" size="small" color="black" />
            </button>
          </li>
        </ul>
        <!--2-->
        <div>
          <button
            id="header-toggle-button"
            @click="toggleMenu"
            class="icon-box"
          >
            <svg width="18" height="18" viewBox="0 0 18 18">
              <polyline
                id="globalnav-menutrigger-bread-bottom"
                fill="none"
                stroke="currentColor"
                stroke-width="1.2"
                stroke-linecap="round"
                stroke-linejoin="round"
                points="2 12, 16 12"
                class="globalnav-menutrigger-bread globalnav-menutrigger-bread-bottom"
              >
                <animate
                  id="globalnav-anim-menutrigger-bread-bottom-open"
                  attributeName="points"
                  keyTimes="0;0.5;1"
                  dur="0.24s"
                  begin="indefinite"
                  fill="freeze"
                  calcMode="spline"
                  keySplines="0.42, 0, 1, 1;0, 0, 0.58, 1"
                  values=" 2 12, 16 12; 2 9, 16 9; 3.5 15, 15 3.5"
                ></animate>
                <animate
                  id="globalnav-anim-menutrigger-bread-bottom-close"
                  attributeName="points"
                  keyTimes="0;0.5;1"
                  dur="0.24s"
                  begin="indefinite"
                  fill="freeze"
                  calcMode="spline"
                  keySplines="0.42, 0, 1, 1;0, 0, 0.58, 1"
                  values=" 3.5 15, 15 3.5; 2 9, 16 9; 2 12, 16 12"
                ></animate>
              </polyline>
              <polyline
                id="globalnav-menutrigger-bread-top"
                fill="none"
                stroke="currentColor"
                stroke-width="1.2"
                stroke-linecap="round"
                stroke-linejoin="round"
                points="2 5, 16 5"
                class="globalnav-menutrigger-bread globalnav-menutrigger-bread-top"
              >
                <animate
                  id="globalnav-anim-menutrigger-bread-top-open"
                  attributeName="points"
                  keyTimes="0;0.5;1"
                  dur="0.24s"
                  begin="indefinite"
                  fill="freeze"
                  calcMode="spline"
                  keySplines="0.42, 0, 1, 1;0, 0, 0.58, 1"
                  values=" 2 5, 16 5; 2 9, 16 9; 3.5 3.5, 15 15"
                ></animate>
                <animate
                  id="globalnav-anim-menutrigger-bread-top-close"
                  attributeName="points"
                  keyTimes="0;0.5;1"
                  dur="0.24s"
                  begin="indefinite"
                  fill="freeze"
                  calcMode="spline"
                  keySplines="0.42, 0, 1, 1;0, 0, 0.58, 1"
                  values=" 3.5 3.5, 15 15; 2 9, 16 9; 2 5, 16 5"
                ></animate>
              </polyline>
            </svg>
          </button>
        </div>
      </div>
    </nav>
  </div>
</template>

<style scoped>
/* 상단 고정 용 */
#global-header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 500;
  background-color: rgba(255, 255, 255, 0.5);
}

/* 헤더 내용물 정렬 */
#global-nav-content {
  display: flex;
  justify-content: center;
  align-items: center;
}

/* 네비게이션 메뉴 아이템을 감싸는 */
.nav-item {
  display: flex;
  justify-content: center;
  align-items: center;
}

/* 네비게이션 아이템 */
.nav-items {
  margin-left: 16px;
  margin-right: 16px;
}
.nav-items i {
  display: none;
}

/* li 태그 중 아이콘인 녀석들*/
.icon-box {
  width: 48px;
  height: 48px;
  display: flex;
  justify-content: center;
  align-items: center;
}

/* ul 태그 */
.ul-item {
  display: flex;
  list-style: none;
}

/* 햄버거 버튼: 화면이 클 때는 렌더링 안함 */
#header-toggle-button {
  display: none;
}

@media (max-width: 768px) {
  /* 헤더 내용물 정렬 */
  #global-nav-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  /* 햄버거 버튼: 화면이 작아지면 렌더링 */
  #header-toggle-button {
    display: flex;
  }

  /* 네비게이션 메뉴 아이템을 감싸는 */
  .nav-item {
    position: fixed;
    z-index: 1000;
    top: 0;
    left: 0;
    padding-top: 64px;
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    background-color: white;
  }

  /* 네비게이션 아이템 */
  .nav-items {
    width: 100%;
    display: flex;
    justify-content: space-between;
    margin: 0;
    padding: 8px 8px 8px 32px;
    font-size: xx-large;
    font-weight: 600;
  }

  .nav-items i {
    display: block;
  }

  .nav-list {
    display: none;
    flex-direction: column;
    width: 100%;
    background-color: rgba(255, 255, 255, 0.5);
    position: absolute;
    top: 60px;
    left: 0;
  }

  .nav-list.active {
    display: flex;
  }

  .menu-toggle {
    display: flex;
  }
}
</style>
