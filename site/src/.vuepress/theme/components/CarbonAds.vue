<script>
export default {
  name: 'CarbonAds',

  watch: {
    '$route' (to, from) {
      if (
        to.path !== from.path
        // Only reload if the ad has been loaded
        // otherwise it's possible that the script is appended but
        // the ads are not loaded yet. This would result in duplicated ads.
        && this.$el.querySelector('#carbonads')
      ) {
        this.$el.innerHTML = ''
        this.load()
      }
    }
  },

  mounted () {
    this.load()
  },

  methods: {
    load () {
      const s = document.createElement('script')
      s.id = '_carbonads_js'
      s.src = `//cdn.carbonads.com/carbon.js?serve=CEADPK37&placement=altairsirmueldesign`
      this.$el.appendChild(s)
    }
  },

  render (h) {
    return h('div', { class: 'carbon-ads' })
  }
}
</script>

<style lang="stylus">
.carbon-ads
  min-height 100px
  padding 1.5rem 1.5rem
  font-size 0.75rem
  max-width 400px
  text-align left
  margin 0 auto
  overflow hidden
  a
    display inline
  .carbon-img
    float left
    margin-right 1rem
    border 1px solid $borderColor
    img
      display block
  .carbon-poweredby
    color #999
    display block
    margin-top 0.5em

@media (max-width: $MQMobile)
  .carbon-ads
    .carbon-img img
      max-width 100px
      max-height 77px
</style>