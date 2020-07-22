<template>
  <div>
    <Hero />
    <Stories />
    <Likes />
    <Uses />
    <Presentation />
    <CapitalGain />
  </div>
</template>

<script>
import {
  Hero,
  CapitalGain,
  Likes,
  Presentation,
  Stories,
  Uses,
} from './components'

export default {
  name: 'HomePageModule',

  components: {
    Hero,
    Stories,
    Likes,
    Uses,
    Presentation,
    CapitalGain,
  },

  mounted() {
    const resizeEvent = () => {
      return (
        window.innerHeight ||
        document.documentElement.clientHeight ||
        document.body.clientHeight
      )
    }
    const inElement = document.querySelectorAll('.fadeIn, .window')

    for (let i = 0; i < inElement.length; i++) {
      const element = inElement[i]
      element.style.opacity = '0'
    }

    const fadeIn = (elements) => {
      for (let i = 0; i < elements.length; i++) {
        const elementTop = elements[i].getBoundingClientRect().top
        const element = elements[i]
        element.style.opacity = '0'

        if (elementTop - resizeEvent() / 1.5 <= 0) {
          element.style.opacity = '1'
        } else if (elementTop - resizeEvent() / 1.5 > 0) {
          element.style.opacity = '0'
        }
      }
    }

    const hero = document.querySelector('.hero')
    const inner = document.querySelector('.inner--hero')

    const parallax = (element, speed) => {
      const topPage = window.pageYOffset
      const bottomParallaxElement = element.scrollHeight
      const pourcent = ((topPage * 100) / bottomParallaxElement / speed) * -1
      const containerEnd = hero.offsetTop + hero.clientHeight

      if (
        resizeEvent() > 600 &&
        topPage < containerEnd &&
        window.innerWidth > 500
      ) {
        element.style.top = 'calc(' + topPage + 'px + ' + pourcent + '%)'
      } else {
        element.style.top = ''
      }
    }

    // check anim
    const checkContainer = document.querySelectorAll('.checkFadeIn')

    const checkAnim = (container) => {
      for (let i = 0; i < container.length; i++) {
        const element = container[i]
        const containerTop = element.getBoundingClientRect().top

        if (containerTop - resizeEvent() / 1.5 <= 0) {
          element.classList.add('check-animate')
        } else if (containerTop - resizeEvent() / 1.5 > 0) {
          element.classList.remove('check-animate')
        }
      }
    }

    window.onscroll = () => {
      checkAnim(checkContainer)
      fadeIn(inElement)
      parallax(inner, 5)
    }
    window.onresize = () => {
      checkAnim(checkContainer)
      fadeIn(inElement)
      parallax(inner, 5)
    }
  },
}
</script>

<style></style>
