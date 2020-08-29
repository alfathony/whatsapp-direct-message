<template>
  <div>
    <v-list three-line>
      <template v-for="(item, index) in items">
        <v-subheader
          v-if="item.header"
          :key="item.header"
          v-text="item.header"
        ></v-subheader>

        <v-divider
          v-else-if="item.divider"
          :key="index"
          :inset="item.inset"
        ></v-divider>

        <v-list-item v-else :key="item.title">
          <v-list-item-avatar>
            <v-img :src="item.avatar"></v-img>
          </v-list-item-avatar>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
            <v-list-item-subtitle>{{ item.subtitle }}</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </template>
    </v-list>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        { header: 'Author' },
        {
          avatar:
            'https://instagram.fcgk18-1.fna.fbcdn.net/v/t51.2885-19/s150x150/75419843_890619514688149_6781081468585115648_n.jpg?_nc_ht=instagram.fcgk18-1.fna.fbcdn.net&_nc_cat=101&_nc_ohc=rSupHxahYNkAX_rN-7m&oh=bcc3bd575b6bebede9395a3bad1e452a&oe=5F38259D',
          title: 'Alfathony',
          subtitle: 'Hybrid Vampire and Warewolf',
        },
        { divider: true, inset: true },
      ],
    }
  },
  head: {
    title: 'Author',
    meta: [
      {
        hid: 'description',
        name: 'description',
        content: 'Author of direct whatsapp tools',
      },
      {
        hid: 'og:title',
        name: 'og:title',
        content: 'Author',
      },
      {
        hid: 'og:description',
        name: 'og:description',
        content: 'Author of direct whatsapp tools',
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

<style></style>
