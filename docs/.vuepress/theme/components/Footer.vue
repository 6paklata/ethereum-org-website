<template>
  <footer class="footer">
    <div class="credits">
      Artwork by
      <a
        href="https://impermanence.co"
        target="_blank"
        rel="noopener noreferrer"
        >Lili Feyerabend</a
      >
      feat.
      <a href="https://ilankatin.com" target="_blank" rel="noopener noreferrer"
        >ilan katin</a
      >,
      <a
        href="https://linktr.ee/mattiacprodukt"
        target="_blank"
        rel="noopener noreferrer"
        >Mattia Cuttini</a
      >,
      <a
        href="https://oficinastk.github.io"
        target="_blank"
        rel="noopener noreferrer"
        >Oficinas TK</a
      >,
      <a href="https://xcopyart.com" target="_blank" rel="noopener noreferrer"
        >XCOPY</a
      >.
    </div>
    <p class="updated-date">{{ lastUpdatedText }}: {{ lastUpdatedDate }}</p>
    <ul>
      <li>
        <a
          href="https://github.com/ethereum"
          target="_blank"
          rel="noopener noreferrer"
          >GitHub</a
        >
      </li>
      <li>
        <a
          href="https://twitter.com/ethereum"
          target="_blank"
          rel="noopener noreferrer"
          >Twitter</a
        >
      </li>
      <li>
        <a
          href="https://www.youtube.com/channel/UCNOfzGXD_C9YMYmnefmPH0g"
          target="_blank"
          rel="noopener noreferrer"
          >YouTube</a
        >
      </li>
      <li>
        <a
          href="https://blog.ethereum.org/"
          target="_blank"
          rel="noopener noreferrer"
          >Blog</a
        >
      </li>
      <li><router-link to="/assets/">Brand Assets</router-link></li>
      <li><router-link to="/privacy-policy/">Privacy Policy</router-link></li>
      <li><router-link to="/terms-of-use/">Terms of Use</router-link></li>
      <li><router-link to="/cookie-policy/">Cookie Policy</router-link></li>
      <li><a href="mailto:press@ethereum.org">Contact</a></li>
      <li><router-link to="/languages/">Language Support</router-link></li>
      <li>
        <a
          href="https://ecosystem.support/"
          target="_blank"
          rel="noopener noreferrer"
          >Ecosystem Support Program</a
        >
      </li>
    </ul>
  </footer>
</template>

<script>
import moment from 'moment'
import { translate } from '../utils/translations'

export default {
  computed: {
    lastUpdatedDate() {
      const pagesSortedByDate = this.$site.pages.sort(
        (a, b) => b.lastUpdated - a.lastUpdated
      )
      moment.locale(this.$lang)
      return moment(pagesSortedByDate[0].lastUpdated).format('MMM DD, YYYY')
    },
    lastUpdatedText() {
      return translate('website-last-updated', this.$lang)
    }
  }
}
</script>

<style lang="stylus" scoped>
@require '../styles/config'

footer
  font-size $fsSmall
  padding 6em 2em 2em 10em

  div.credits
    display none
    margin-bottom 0.5em
    color $subduedColor

    a
      color $subduedColor

      &:hover
        color $accentColor

  &.home
    margin-left 2em

    div.credits
      display block

  p.updated-date
    color $subduedColor
    margin 1em 0

  ul
    margin 0

    li
      display inline-block
      margin-right 2em

      &:first-child
        padding 0

      &:before
        content ''
        padding 0

      a
        color $subduedColor

        &:hover
          color $accentColor

@media (min-width: $breakS)
  footer
    ul
      display flex
      flex-wrap wrap

      li
        padding-left 0
        margin-bottom 1em
</style>
