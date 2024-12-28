---
layout: page
---

<script setup>
import {
  VPTeamPage,
  VPTeamPageTitle,
  VPTeamMembers,
  VPTeamPageSection,
} from 'vitepress/theme'

const linkIcon = { 
    svg: '<svg t="1709478143088" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="4794"><path d="M574 665.4c-3.1-3.1-8.2-3.1-11.3 0L446.5 781.6c-53.8 53.8-144.6 59.5-204 0-59.5-59.5-53.8-150.2 0-204l116.2-116.2c3.1-3.1 3.1-8.2 0-11.3l-39.8-39.8c-3.1-3.1-8.2-3.1-11.3 0L191.4 526.5c-84.6 84.6-84.6 221.5 0 306s221.5 84.6 306 0l116.2-116.2c3.1-3.1 3.1-8.2 0-11.3L574 665.4zM832.6 191.4c-84.6-84.6-221.5-84.6-306 0L410.3 307.6c-3.1 3.1-3.1 8.2 0 11.3l39.7 39.7c3.1 3.1 8.2 3.1 11.3 0l116.2-116.2c53.8-53.8 144.6-59.5 204 0 59.5 59.5 53.8 150.2 0 204L665.3 562.6c-3.1 3.1-3.1 8.2 0 11.3l39.8 39.8c3.1 3.1 8.2 3.1 11.3 0l116.2-116.2c84.5-84.6 84.5-221.5 0-306.1z" p-id="4795"></path><path d="M610.1 372.3c-3.1-3.1-8.2-3.1-11.3 0L372.3 598.7c-3.1 3.1-3.1 8.2 0 11.3l39.6 39.6c3.1 3.1 8.2 3.1 11.3 0l226.4-226.4c3.1-3.1 3.1-8.2 0-11.3l-39.5-39.6z" p-id="4796"></path></svg>'
}
  
const ops = [
  {
    avatar: '/avatar/jianyuehugo.jpg',
    name: 'JianyueHugo',
    title: '技术组组长',
    links: [
      { icon: 'github', link: 'https://github.com/JianyueLab' },
      { icon: linkIcon, link: 'https://jhl.idv.hk' }
    ]
  },
  {
    avatar: '/avatar/lyofficial.png',
    name: 'LYOfficial',
    title: '总管/翻译组组长',
    links: [
      { icon: 'github', link: 'https://github.com/LYOfficial' },
      { icon: linkIcon, link: 'https://blog.coldregion.top' },
    ]
  },
  {
    avatar: '/avatar/pangpi.png',
    name: 'pipigod',
    title: '技术组组员',
    links: [
      { icon: 'github', link: 'https://github.com/pangpilolo' },
      { icon: linkIcon, link: 'https://paofull.cn' },
    ]
  },
]

const translator = [
  {
    avatar: '/avatar/dazidian.jpg',
    name: 'DaZiDian',
    title: '翻译组成员',
    links: [
      { icon: 'github', link: 'https://github.com/dazidian' },
      { icon: linkIcon, link: 'https://dz1d.space' },
    ]
  },
  {
    avatar: '/avatar/sky_tianle.jpg',
    name: 'sky_tianle',
    title: '翻译组副组长',
    links: [
      { icon: 'github', link: 'https://github.com/skytianle666' },
    ]
  },
  {
    avatar: '/avatar/jianyuehugo.jpg',
    name: 'JianyueHugo',
    title: '技术组组长',
    links: [
      { icon: 'github', link: 'https://github.com/JianyueLab' },
      { icon: linkIcon, link: 'https://jhl.idv.hk' }
    ]
  },
  {
    avatar: '/avatar/lyofficial.png',
    name: 'LYOfficial',
    title: '总管/翻译组组长',
    links: [
      { icon: 'github', link: 'https://github.com/LYOfficial' },
      { icon: linkIcon, link: 'https://blog.coldregion.top' },
    ]
  },
  {
    avatar: '/avatar/annijang.jpg',
    name: 'annijang',
    title: '翻译组成员',
    links: [
      { icon: 'github', link: 'https://github.com/annijang' },
    ]
  },
]
</script>

<VPTeamPage>
  <VPTeamPageSection>
    <template #title>技术</template>
    <template #lead>网站维护</template>
    <template #members>
      <VPTeamMembers size="small" :members="ops" />
    </template>
  </VPTeamPageSection>
  <VPTeamPageSection>
    <template #title>翻译</template>
    <template #lead>文档翻译</template>
    <template #members>
      <VPTeamMembers size="small" :members="translator" />
    </template>
  </VPTeamPageSection>
</VPTeamPage>
