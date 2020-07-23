<template>
  <div>
    <Hero :data="HeroData" />
    <Stories :data="StoriesData" />
    <Likes :data="LikesData" />
    <Uses :data="ToolsData" />
    <Presentation :data="PresentationData" />
    <CapitalGain :data="CapitalGainData" />
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

  props: {
    data: {
      type: Object,
      required: true,
    },
  },

  data() {
    return {
      HeroData: {
        hello: this.data.hero_hello,
        title: this.data.hero_title,
        subtitle: this.data.hero_subtitle,
        end_word: this.data.hero_end_word,
      },
      StoriesData: {
        title: this.data.stories_title,
        subtitle: this.data.stories_subtitle,
        stories: this.data.stories,
      },
      LikesData: {
        title: this.data.likes_title,
        hobbies: this.data.likes_hobbies,
      },
      ToolsData: {
        title: this.data.tools_title,
        subtitle: this.data.tools_subtitle,
        windows: this.data.body,
        logo_list: this.data.tools_logo_list,
      },
      PresentationData: {
        title: this.data.who_title,
        subtitle: this.data.who_subtitle,
      },
      CapitalGainData: {
        you_for_me: {
          title: this.data.you_for_me_title,
          subtitle: this.data.you_for_me_subtitle,
          card_title: this.data.you_for_me_card_title,
          card_item: this.data.you_for_me_card_item,
        },
        me_for_you: {
          title: this.data.me_for_you_title,
          subtitle: this.data.me_for_you_subtitle,
          card_title: this.data.me_for_you_card_title,
          card_item: this.data.me_for_you_card_item,
        },
      },
    }
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
