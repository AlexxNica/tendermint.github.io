<template>
  <div class="page-split page-career-index">
    <page-header
      title="Careers"
      subtitle="Work with us to improve Tendermint."
      type="split"
      theme="tendermint">
      <div class="tags">
        <div id="tag-all" class="tag active" @click="setActiveTag($event)">all</div>
        <div class="tag" v-for="tag in tags" @click="setActiveTag($event,tag)">{{ tag }}</div>
      </div>
    </page-header>

    <section class="section-default page-content">
      <div class="section-container">
        <div class="section-content">
          <card-post v-for="career in filteredCareers" :url="'/careers/' + career.id"
            :title="career.title" :desc="career.subtitle">
          </card-post>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import PageHeader from '@nylira/vue-page-header'
import { mapGetters } from 'vuex'
import { union, orderBy } from 'lodash'
import $ from 'jquery'
import CardPost from './CardPost'
export default {
  name: 'page-career-index',
  components: {
    PageHeader,
    CardPost
  },
  computed: {
    tags () {
      let tags = []
      this.careers.map(function (career) {
        tags = union(tags, career.tags)
      })
      return tags
    },
    filteredCareers () {
      let activeTag = this.activeTag
      let orderedCareers = orderBy(this.careers, ['weight'], ['asc'])

      if (activeTag === 'all') {
        return orderedCareers
      } else {
        return orderedCareers.filter(career => career.tags.includes(activeTag))
      }
    },
    ...mapGetters({
      careers: 'allCareers'
    })
  },
  data () {
    return {
      activeTag: 'all'
    }
  },
  methods: {
    setActiveTag ($event, tagName) {
      $('.tag').removeClass('active')
      if (tagName) {
        $($event.target).addClass('active')
        this.activeTag = tagName
        return
      }
      $('#tag-all').addClass('active')
      this.activeTag = 'all'
      return
    }
  },
  mounted () {
    document.title = 'Careers - Tendermint'
  }
}
</script>


<style lang="stylus">
@require '../styles/variables.styl'

.page-career-index
  .tags
    margin-top 1rem
    text-align center
    max-width 40*x
    display flex
    flex-flow row wrap

  .tag
    font-size 0.75*x
    background lighten(bc, 50%)
    color dim
    margin-right 0.25*x
    margin-bottom 0.25*x
    padding 0.25*x 0.5*x

    cursor pointer

    background hsla(0,0,0,25%)
    color #fff
    &.active
      background darken(acolor,25%)

@media screen and (min-width: 720px)
  .page-career-index
    .tag
      font-size x

@media screen and (min-width: 960px)
  .page-career-index
    .tags
      justify-content flex-start
</style>
