<template>
  <div>
    <div class="my-6">
      <p>
        Send whatsapp without save number
        <span class="caption d-block">Available for Indonesia only</span>
      </p>
    </div>

    <v-text-field
      v-model="phoneNumber"
      dark
      outlined
      clearable
      solo
      single-line
      placeholder="Phone number"
      prefix="+62"
      type="number"
      :error="error"
      :autofocus="focus"
    ></v-text-field>

    <v-btn block large @click="sendMessage">Send Message</v-btn>

    <v-snackbar v-model="snackbar">
      {{ snackbarText }}

      <template v-slot:action="{ attrs }">
        <v-btn color="pink" text v-bind="attrs" @click="snackbar = false">
          Close
        </v-btn>
      </template>
    </v-snackbar>
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      error: false,
      phoneNumber: null,
      focus: true,
      snackbar: false,
      snackbarText: "Hello, I'm a snackbar",
    }
  },
  methods: {
    sendMessage() {
      if (this.phoneNumber) {
        this.error = false
        const value = this.phoneNumber

        // slice first character
        const firstChar = value.slice(0, 1)
        const fullChar = value.slice(1, 15)

        let fullPhoneNumber = null

        if (firstChar === 0) {
          fullPhoneNumber = fullChar
        } else {
          fullPhoneNumber = this.phoneNumber
        }

        window.location.href =
          'https://api.whatsapp.com/send?phone=62' + fullPhoneNumber
      } else {
        this.error = true
        this.snackbarText = 'Input phone number'
        this.snackbar = true
      }
    },
  },
  head: {
    title: 'Direct Whatsapp',
    meta: [
      {
        hid: 'description',
        name: 'description',
        content: 'Kirim pesan whatsapp tanpa menyimpan nomor telepon',
      },
    ],
    noscript: [{ innerHTML: 'Body No Scripts', body: true }],
    script: [
      { src: '/head.js' },
      // Supported since 1.0
      { src: '/body.js', body: true },
      { src: '/defer.js', defer: '' },
    ],
  },
}
</script>

<style scoped></style>
