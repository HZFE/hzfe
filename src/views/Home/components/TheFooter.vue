<template>
  <section class="footer">
    <div class="social">
      <Icon name="weibo" href="https://weibo.com/hzfestudio" class="icons"/>  
      <Icon name="github" href="https://github.com/hzfe" class="icons"/>  
    </div>
    <div class="copyright">© {{ year }} HZFEStudio 已成立{{ establishedDays }}天</div>
  </section>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator'
import Icon from './Icon.vue'

@Component({
  components: { Icon }
})
export default class TheFooter extends Vue {
  get establishedDays () {
    const birthday = +new Date('2016-09-14')
    const nowTime = +new Date()
    const day2Msec = 24 * 60 * 60 * 1000

    return Math.round((nowTime - birthday) / day2Msec)
  }
  get year () {
    const yearNow = new Date().getFullYear()
    return yearNow
  }
}
</script>

<style scoped lang="scss">
  @import '~style';

  .footer {
    background-color: $blue-ink;
    @include flex-cross-center;
    justify-content: space-between;

    padding: $gap-normal $gap-big;
    color: rgba(255,255,255,.4);
    font-size: 14px;
  }
  .social {
    display: flex;
    align-items: center;
  }
  .icons {
    margin-right: 5px;
  }
  @include max-screen($media-ip6p) {
    .footer {
      padding: $gap-normal $gap-small;
    }
  }
</style>
