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
        <v-list style="margin: 0 auto; max-width: 1000px">
          <v-list-group
            v-for="(item, i) in faqItems"
            :key="item.title"
            v-model="item.active"
            no-action
            color="#00ffff"
          >
            <template v-slot:activator>
              <v-list-item-icon
                style="margin: 0 24px 0 0; align-self: center;"
              >
                Q.{{ i + 1 }}
              </v-list-item-icon>
              <v-list-item-content>
                <v-list-item-title
                  style="text-align: left; white-space: normal; line-height: 1em;"
                >
                  {{ item.question }}
                </v-list-item-title>
              </v-list-item-content>
            </template>

            <v-list-item style="padding: 0 16px 0 32px;">
              <v-list-item-icon
                style="margin: 0 24px 0 0; align-self: center;"
              >
                A.{{ i + 1 }}
              </v-list-item-icon>
              <v-list-item-content>
                <v-list-item-title
                  style="text-align: left; white-space: normal; line-height: 1em;"
                >
                  {{ item.answer }}
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
      title: 'Q & A',
      faqItems: [
        {
          question: 'よくある質問（FAQ）とはどのようなものでしょうか？',
          answer: 'よくある質問とは、よくある(あるいはあると想定される)質問とその回答とを集めたもののことです。'
        },
        {
          question: 'Question2',
          answer: 'Answer2'
        },
        {
          question: 'Question3',
          answer: 'Answer3'
        }
      ]
    }
  }
}
</script>
