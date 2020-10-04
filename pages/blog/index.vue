<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <v-flex
      xs12
      sm8
      md6
    >
      <div class="text-center">
        <h1>ブログページ</h1>
        <h2>※ 仮作成のため、表示内容にはNote公式のページを利用しています</h2>
        <h2 v-if="noteItems.length == 0">
          ブログを読み込み中
        </h2>
        <ul v-else>
          <li
            v-for="item in noteItems"
            :key="item.link"
            style="text-align: left;"
          >
            <h2>{{ item.title }}</h2>
            <!-- <img style="width: 300px" :src="item.img" /> -->
          </li>
        </ul>
      </div>
    </v-flex>
  </v-layout>
</template>

<style scoped>
</style>

<script>
import axios from 'axios'
import xml2js from 'xml2js'

export default {
  data () {
    return {
      title: 'Blog',
      noteItems: []
    }
  },
  async mounted () { // Noteの取得
    const xmlUrl = 'https://friendly-yalow-4a2e2c.netlify.app/.netlify/functions/note'
    const xmlText = await axios.get(xmlUrl)
      .then((res) => { return res.data })
      .catch(() => { return '' })

    const parser = new xml2js.Parser({
      async: false,
      explicitArray: false
    })

    let xmlObj = null
    parser.parseString(xmlText, (_, json) => {
      xmlObj = json
    })

    this.noteItems = xmlObj ? xmlObj.rss.channel.item.map((v) => {
      return {
        title: v.title,
        img: v['media:thumbnail'],
        link: v.link,
        description: v.description
      }
    }) : []
  }
}
</script>
