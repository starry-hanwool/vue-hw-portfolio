<template>
  <v-dialog v-model="dialog" max-width="1200">
    <template #activator="{ on, attrs }">
      <v-btn color="primary" v-bind="attrs" v-on="on"> 더보기 </v-btn>
    </template>

    <v-card outlined style="overflow-x: hidden">
      <v-card-title class="headline primary white--text">
        {{ project.title }}
      </v-card-title>

      <v-row class="">
        <v-col cols="12" sm="6" md="6" lg="6">
          <v-card-text>
            <v-carousel :height="600">
              <v-carousel-item
                v-for="(item, i) in project.imgs"
                :key="i"
                :src="item.src"
                contain
              ></v-carousel-item>
            </v-carousel>
          </v-card-text>
        </v-col>
        <v-col cols="12" sm="6" md="6" lg="6">
          <v-card-text class="info">
            <v-row class="mx-0">
              <v-col cols="1">
                <v-icon small>fas fa-calendar-check</v-icon>
              </v-col>
              <v-col>
                <div class="ml-3">{{ project.period }}</div>
              </v-col>
            </v-row>
            <v-row class="mx-0">
              <v-col cols="1">
                <v-icon small>fas fa-child</v-icon>
              </v-col>
              <v-col>
                <div class="ml-3">{{ project.team }}</div>
              </v-col>
            </v-row>
            <v-row class="mx-0">
              <v-col cols="1">
                <v-icon small>fas fa-clipboard-list</v-icon>
              </v-col>
              <v-col>
                <div v-for="charge in project.charge" :key="charge.subject">
                  <div class="ml-3">
                    {{ charge.subject }}
                  </div>

                  <div class="blue-grey--text text--darken-2 ml-3 my-2">
                    <ul v-for="content in charge.content" :key="content">
                      <li>{{ content }}</li>
                    </ul>
                  </div>
                </div>
              </v-col>
            </v-row>
            <v-row class="mx-0">
              <v-col cols="1">
                <v-icon small>fas fa-hdd</v-icon>
              </v-col>
              <v-col v-for="skill in project.skills" :key="skill.subject">
                <div>
                  <div class="ml-3">
                    {{ skill.subject }}
                  </div>

                  <div class="blue-grey--text text--darken-2 ml-3 my-2">
                    <ul v-for="content in skill.content" :key="content">
                      <li>{{ content }}</li>
                    </ul>
                  </div>
                </div>
              </v-col>
            </v-row>
          </v-card-text>
        </v-col>
      </v-row>

      <v-divider></v-divider>

      <v-card-actions class="justify-end">
        <v-btn color="accent" text @click="dialog = false"> Close </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  name: 'ImageSliderDialog',
  props: {
    project: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      dialog: false,
    }
  },
}
</script>

<style scoped></style>
