<template></template>

<script>
/* global BASEURL */
/* global STRIPURL */

export default {
  created() {
    if (typeof this.$ssrContext !== "undefined") {
      this.$ssrContext.userHeadTags += `<link rel='canonical' href='${this.computeURL()}'/>`;
    }
  },
  methods: {
    computeURL() {
      let pagePath = STRIPURL
        ? this.$page.path.replace(/\.html$/, "")
        : this.$page.path;
      return BASEURL + pagePath;
    }
  }
};
</script>