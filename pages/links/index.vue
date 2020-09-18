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
      style="width: 100%;"
    >
      <div class="text-center">
        <h1>Welcom to {{ title }} Page</h1>
        <v-list style="margin: 0 auto; max-width: 700px">
          <v-list-group
            v-for="(linkGroupItem) in linkGroupItems"
            :key="linkGroupItem.groupName"
            no-action
            sub-group
            value="true"
            color="#ffffff"
          >
            <template v-slot:activator>
              <v-list-item-content>
                <v-list-item-title
                  style="text-align: left; white-space: normal; line-height: 1em;"
                >
                  {{ linkGroupItem.groupName }}
                </v-list-item-title>
              </v-list-item-content>
            </template>

            <v-list-item
              v-for="(linkItem) in linkGroupItem.linkItems"
              :key="linkItem.text"
              style="padding: 0 16px 0 64px;"
            >
              <v-list-item-content>
                <v-list-item-title
                  style="text-align: left; white-space: normal; line-height: 1em;"
                >
                  <a :href="linkItem.link">{{ linkItem.text }}</a>
                </v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-group>
        </v-list>
      </div>
    </v-flex>
  </v-layout>
</template>

<style scoped>
</style>

<script>
export default {
  data () {
    return {
      title: 'Links',
      linkGroupItems: [
        {
          groupName: 'N高公式',
          linkItems: [
            {
              text: 'N高ホームページ',
              link: 'https://nnn.ed.jp/'
            }
          ]
        },
        {
          groupName: 'N高友好同好会',
          linkItems: [
            {
              text: '写真同好会',
              link: 'http://syadou.wp.xdomain.jp/'
            }
          ]
        }
      ]
    }
  }
}
</script>
