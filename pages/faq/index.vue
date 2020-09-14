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
        <h1>Welcom to {{ title }} Page</h1>
        <!-- <v-list-group
          v-for="(item, i) in faqItems"
          :key="i"
          value="true"
          no-action
        >
          <template v-slot:activator>
            <v-list-item-title>{{ item.question }}</v-list-item-title>
          </template>
          <v-list-item
            link
          >
            <v-list-item-title>{{ item.answer }}</v-list-item-title>
          </v-list-item>
        </v-list-group> -->
        
        <v-list>
          <v-list-group
            v-for="item in faqItems"
            :key="item.title"
            v-model="item.active"
            no-action
          >
            <template v-slot:activator>
              <v-list-item-content>
                <v-list-item-title v-text="item.question"></v-list-item-title>
              </v-list-item-content>
            </template>

            <v-list-item>
              <v-list-item-content>
                <v-list-item-title v-text="item.answer"></v-list-item-title>
              </v-list-item-content>
            </v-list-item>
          </v-list-group>
        </v-list>
      </div>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  data () {
    return {
      title: 'Q & A',
      faqItems: [
        {
          question: 'Question1',
          answer: 'Answer1'
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
