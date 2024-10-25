<script setup>
import { ref } from 'vue'

const isMenuClose = ref(true)

const isSubMenuClose = ref(true)
const isSearchClose = ref(true)

const toggleMenu = () => {
  isMenuClose.value = !isMenuClose.value

  if (isMenuClose.value) {
    document
      .getElementById('appbar-nav-anim-menu-trigger-bread-bottom-close')
      .beginElement()
    document
      .getElementById('appbar-nav-anim-menu-trigger-bread-top-close')
      .beginElement()
  } else {
    document
      .getElementById('appbar-nav-anim-menu-trigger-bread-bottom-open')
      .beginElement()
    document
      .getElementById('appbar-nav-anim-menu-trigger-bread-top-open')
      .beginElement()
  }
}

const toggleSearch = () => {
  isSubMenuClose.value = !isSubMenuClose.value
  isSearchClose.value = !isSearchClose.value
}

const navItems = [
  { text: '지역', link: '#' },
  { text: '여행코스', link: '#' },
]

const searchResultItems = [
  { text: '결과1', link: '/' },
  { text: '결과2', link: '/' },
  { text: '결과3', link: '/' },
]

const historyItems = [
  { text: '기록1', link: '/' },
  { text: '기록2', link: '/' },
  { text: '기록3', link: '/' },
]
</script>

<template>
  <div id="appbar-header">
    <nav id="appbar-nav">
      <div id="appbar-content">
        <!--1-->
        <ul class="appbar-ul-item">
          <!--로고-->
          <li>
            <RouterLink to="/" class="appbar-icon-box">
              <img alt="Trip logo" src="@/assets/23532_color.svg" width="30" />
            </RouterLink>
          </li>
          <!--메뉴-->
          <li class="appbar-nav-item" :class="{ show: !isMenuClose }">
            <div
              class="appbar-nav-items"
              v-for="(item, index) in navItems"
              :key="index"
            >
              <div>{{ item.text }}</div>
              <v-icon icon="mdi-chevron-right"></v-icon>
            </div>
          </li>
          <!--돋보기-->
          <li class="appbar-ul-items-right">
            <button class="appbar-icon-box" @click="toggleSearch">
              <v-icon icon="mdi-magnify" size="small" color="black" />
            </button>
            <!--검색 서브 메뉴-->
            <div id="appbar-submenu-search" >
              <div class="appbar-submenu-content" :class="{show: isSubMenuClose}">
                <!--검색창-->
                <div class="appbar-submenu-content-item pt-2">
                  <v-icon icon="mdi-magnify" size="large" color="black" />
                  <input
                    type="text"
                    autocomplete="off"
                    autofocus
                    name="search"
                    class="appbar-submenu-content-search-input"
                    placeholder="잡아라! 트립핑!"
                  />
                </div>
                <!--결과창-->
                <div class="appbar-submenu-content-subtitle">결과</div>
                <div
                  class="appbar-submenu-content-item"
                  v-for="(item, index) in searchResultItems"
                  :key="index"
                >
                  <RouterLink :to="item.link" class="appbar-submenu-content-item">
                    <v-icon icon="mdi-arrow-right" size="x-small"></v-icon>
                    <div>{{ item.text }}</div>
                  </RouterLink>
                </div>

                <!--검색기록-->
                <div class="appbar-submenu-content-subtitle">기록</div>
                <div
                  v-for="(item, index) in historyItems"
                  :key="index"
                >
                  <RouterLink :to="item.link" class="appbar-submenu-content-item">
                    <v-icon icon="mdi-arrow-right" size="x-small"></v-icon>
                    <div>{{ item.text }}</div>
                  </RouterLink>
                </div>
              </div>
            </div>
          </li>
          <!--즐겨찾기-->
          <li>
            <button class="appbar-icon-box">
              <v-icon icon="mdi-star-outline" size="small" color="black" />
            </button>
            <!--즐겨찾기 서브 메뉴-->
          </li>
        </ul>
        <!--2-->
        <div id="appbar-header-toggle">
          <button @click="toggleMenu" class="appbar-icon-box">
            <svg width="18" height="18" viewBox="0 0 18 18">
              <polyline
                id="global-nav-menu-trigger-bread-bottom"
                fill="none"
                stroke="currentColor"
                stroke-width="1.2"
                stroke-linecap="round"
                stroke-linejoin="round"
                points="2 12, 16 12"
                class="global-nav-menu-trigger-bread global-nav-menu-trigger-bread-bottom"
              >
                <animate
                  id="appbar-nav-anim-menu-trigger-bread-bottom-open"
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
                  id="appbar-nav-anim-menu-trigger-bread-bottom-close"
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
                id="global-nav-menu-trigger-bread-top"
                fill="none"
                stroke="currentColor"
                stroke-width="1.2"
                stroke-linecap="round"
                stroke-linejoin="round"
                points="2 5, 16 5"
                class="global-nav-menu-trigger-bread global-nav-menu-trigger-bread-top"
              >
                <animate
                  id="appbar-nav-anim-menu-trigger-bread-top-open"
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
                  id="appbar-nav-anim-menu-trigger-bread-top-close"
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
#appbar-header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 500;
  background-color: rgba(255, 255, 255, 0.5);
}

/* 헤더 내용물 정렬 */
#appbar-content {
  display: flex;
  justify-content: center;
  align-items: center;
}

/* 네비게이션 메뉴 아이템을 감싸는 */
.appbar-nav-item {
  display: flex;
  justify-content: center;
  align-items: center;
}

/* 네비게이션 아이템 */
.appbar-nav-items {
  margin-left: 16px;
  margin-right: 16px;
}

.appbar-nav-items i {
  display: none;
}

/* li 태그 중 아이콘인 녀석들*/
.appbar-icon-box {
  width: 48px;
  height: 48px;
  display: flex;
  justify-content: center;
  align-items: center;
}

/* ul 태그 */
.appbar-ul-item {
  display: flex;
  list-style: none;
}

/* 햄버거 버튼: 화면이 클 때는 렌더링 안함 */
#appbar-header-toggle {
  display: none;
}


/* 검색 서브 메뉴 */
#appbar-submenu-search {
  position: fixed;
  width: 100%;
  top: 48px;
  left: 0;
}

/* 검색 서브 메뉴 내용 */
.appbar-submenu-content {
  overflow: hidden;
  height: 0;
  background-color: white;
  padding-left: 10vw;
  padding-right: 10vw;
  margin-top: 10vw;
  transition: height 1s ease;
}

.appbar-submenu-content.show {
  overflow: visible;
  height: auto;
}

/* 검색 서브 메뉴 내용 중 링크 */
.appbar-submenu-content-item {
  display: flex;
  gap: 10px;
  justify-content: left;
  align-items: center;
  text-decoration: none;
  color: black;
  font-size: small;
}

/* 검색 서브 메뉴 내용 중 서브 타이틀 */
.appbar-submenu-content-subtitle {
  font-size: small;
  font-weight: 400;
  color: gray;
  padding-top: 32px;
  padding-bottom: 8px;
}

.appbar-submenu-content-search-input {
  border: none;
  font-size: x-large;
}
.appbar-submenu-content-search-input:focus {
  outline: none;
}

@media (max-width: 768px) {
  /* 헤더 내용물 정렬 */
  #appbar-content {
    justify-content: left;
  }

  .appbar-ul-item {
    width: calc(100% - 48px);
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  /* 햄버거 버튼: 화면이 작아지면 렌더링 */
  #appbar-header-toggle {
    display: block;
    position: fixed;
    z-index: 1001;
    top: 0;
    right: 0;
  }

  /* 네비게이션 메뉴 아이템을 감싸는 */
  .appbar-nav-item {
    position: fixed;
    height: 100vh;
    z-index: 1000;
    top: -100%;
    left: 0;
    padding-top: 64px;
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: flex-start;
    background-color: white;
    transition: top 0.5s ease;
  }

  /* 클래스 추가 시 애니메이션 실행 */
  .appbar-nav-item.show {
    top: 0;
  }

  /* 네비게이션 아이템 */
  .appbar-nav-items {
    width: 100%;
    display: flex;
    justify-content: space-between;
    margin: 0;
    padding: 8px 32px 8px 32px;
    font-size: xx-large;
    font-weight: 600;
  }

  .appbar-nav-items i {
    display: block;
  }

  .appbar-ul-items-right {
    margin-left: auto;
  }
}
</style>
