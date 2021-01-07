<template>
  <div>
    <h1> {{mess}} </h1>
    <button v-bind:disabled="disabledSubmit" v-on:click="greet"> SHOW UP</button>
    <p> {{currentRange.start}} </p>
    <input v-model="currentRange.start" placeholder="edit">
  </div>
</template>

<script>
/* eslint-disable */
const Message = {
  props: {
    mess: {
      type: String,
      default: null
    },

    disabledSubmit: {
      type: Boolean,
      default: false
    }
  },

  data () {
    return {
      startDate: '',
      endDate: '',
      currentRange: {
        start: null,
        end: null
      }
    };
  },
  methods: {
    greet: function(event) {
      this.startDate = null;
      console.log("got here")
    }
  },

  name: 'Message',
  computed: {
    startDateObj () {
      // return parseDate(this.startDate, FILTER_FORMAT);
      return
    },

    endDateObj () {
      // return parseDate(this.endDate, FILTER_FORMAT);
      return
    }
  },

  watch: {
    startDate: {
      immediate: true,
      handler () {
        this.currentRange = {...this.currentRange, start: this.startDateObj}
      },
    },

    endDate: {
      immediate: true,
      handler () {
        this.currentRange = {...this.currentRange, end: this.endDateObj}
      }
    },

    currentRange: {
      immediate: true,
      handler: function (newRange, oldRange) {
        console.log("cur eange here")
        if (oldRange && oldRange.start && oldRange.end && newRange.start === oldRange.start && newRange.end === oldRange.end) {
          return
        }
        if (newRange.start || newRange.end) {
          // choosing an explict range should de-select any preset ranges.
          console.log(`What is this`)
        }
      },
    }
  }


}

export default Message
</script>

<style scoped>

</style>
