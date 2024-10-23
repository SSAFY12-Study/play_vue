<script setup>
import { onMounted } from 'vue'

onMounted(() => {
  if (CSS.supports('animation-timeline: view()')) {
    const $sectionPin = document.querySelector('#sectionPin')
    const $pinWrapSticky = document.querySelector('.pin-wrap-sticky')
    const $pinWrap = document.querySelector('.pin-wrap')

    /* Stretch it out, so that we create room for the horizontal scroll animation */
    $sectionPin.style.height = '500vh'
    $sectionPin.style.overflow = 'visible' // To make position sticky work …

    /* Stick to Top */
    $pinWrapSticky.style.height = '100vh'
    $pinWrapSticky.style.width = '100vw'
    $pinWrapSticky.style.position = 'sticky'
    $pinWrapSticky.style.top = '0'
    $pinWrapSticky.style.overflowX = 'hidden'

    /* Stretch out pinwrap */
    $pinWrap.style.height = '100vh'
    $pinWrap.style.width = '250vmax'

    // Scroll-Linked Animation
    $pinWrap.animate(
      {
        transform: [``, `translateX(calc(-100% + 100vw))`],
      },
      {
        timeline: new ViewTimeline({
          subject: $sectionPin,
          axis: 'block',
        }),
        fill: 'forwards',
        rangeStart: `contain 0%`,
        rangeEnd: `contain 100%`,
      },
    )
  }
})
</script>

<template>
  <body>
    <div class="container ">
      <section>
        <div>
          <h1>
            <span>catch</span>
            <span>trip</span>
            <span>ping</span>
          </h1>
          <p>with boni hyugi</p>
        </div>
      </section>

      <section id="sectionPin">
        <div class="pin-wrap-sticky">
          <div class="pin-wrap">
            <h2>
              Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
              eiusmod tempor incididunt ut labore et dolore magna aliqua.
            </h2>
            <img
              src="https://images.pexels.com/photos/18495179/pexels-photo-18495179/free-photo-of-seoul-at-night.jpeg?auto=compress&cs=tinysrgb&h=900"
              alt=""
            />
            <img
              src="https://images.pexels.com/photos/6312123/pexels-photo-6312123.jpeg?auto=compress&cs=tinysrgb&h=900"
              alt=""
            />
            <img
              src="https://images.pexels.com/photos/19714663/pexels-photo-19714663/free-photo-of-bookshelves-in-the-starfield-library-seoul-south-korea.jpeg?auto=compress&cs=tinysrgb&h=900"
              alt=""
            />
          </div>
        </div>
      </section>

      <section>
        <img
          src="https://images.pexels.com/photos/19543591/pexels-photo-19543591/free-photo-of-gyeongbokgung-palace-at-autumn-dusk.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
          alt=""
        />
        <h2 class="credit">
          <a href="https://thisisadvantage.com" target="_blank"
            >Made by Advantage</a
          >
        </h2>
      </section>
    </div>

    <!--    <RouterLink class="text-h1 text-decoration-none" to="/login"-->
    <!--      >로그인-->
    <!--    </RouterLink>-->
  </body>
</template>

<style scoped>
@layer orig {

  .container {
    color: black;
    transition: 0.3s ease-out;
    max-width: 100vw;
    width: 100%;
    overscroll-behavior: none;
  }

  .container section {
    min-height: 100vh;
    width: 100%;
    max-width: 100vw;
    overflow-x: hidden;
    position: relative;
  }

  .container img {
    height: 78.5vh;
    width: auto;
    max-width: 100%;
    object-fit: cover;
  }

  .container h1 {
    font-family: 'Monoton', 'Noto Sans KR', sans-serif;
    font-size: clamp(1.5rem, 8vw + 1rem, 6rem);
    line-height: 1;
    font-weight: 400;
    margin-bottom: 1rem;
    position: absolute;
    top: 10vw;
    left: 10vw;
    z-index: 4;
    overflow-wrap: break-word;
    hyphens: auto;
  }

  .container h1 span {
    display: block;
  }

  .container h2 {
    font-size: 2rem;
    max-width: 400px;
  }

  .container > p {
    position: absolute;
    bottom: 10vw;
    right: 10vw;
    width: 200px;
    line-height: 1.5;
  }

  .container * {
    box-sizing: border-box;
  }

  .credit a {
    color: black;
  }

  section:not(#sectionPin, .pin-wrap-sticky) {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    grid-gap: 2rem;
    padding: 50px 10vw;
    margin: auto;
    place-items: center;
  }

  #sectionPin {
    height: 100vh;
    display: flex;
    background: black;
    color: aliceblue;
    overflow: scroll;
  }

  .pin-wrap {
    height: 100vh;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    padding: 50px 10vw;
  }

  .pin-wrap > * {
    min-width: 60vmax;
    padding: 0 5vmax;
  }

}
</style>
