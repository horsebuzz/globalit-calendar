<template>
  <div class="wrapper">
    <p class="title">
      <span v-if="event.link && displayHref">
        <a :href="event.link">
          <span v-if="displayIndex">{{index+1}}. </span>{{event.title}}
        </a>
      </span>
      <span v-else>
        <span v-if="displayIndex">{{index+1}}. </span>{{event.title}}
      </span>
      <span class="time">{{dateTimeFormatter(Date.parse(new Date(event.date)),i18n[locale].fullFormat)}}</span>
    </p>
    <p v-if="displayDesc" class="desc">{{event.desc}}</p>
  </div>
</template>
<script>
import i18n from '../i18n.js'
import { dateTimeFormatter } from '../tools.js'
export default {
  data () {
    return {
      i18n
    }
  },
  props: {
    event: {
      type: Object,
      required: true
    },
    index: {
      type: Number,
      required: true
    },
    locale: {
      type: String,
      required: true
    },
    displayIndex: {
      type: Boolean,
      required: true
    },
    displayHref: {
      type: Boolean,
      required: true
    },
    displayDesc: {
      type: Boolean,
      required: true
    }
  },
  methods: {
    dateTimeFormatter
  }
}
</script>
