<template>
  <article class="card">
    <div class="card__image_wrapper">
      <img
        src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw=="
        :alt="alternativeText"
        v-lazyload="imagesrc"
        class="card__image_wrapper__image"
      />
    </div>
    <div class="card__content_wrapper">
      <small class="card__content_wrapper__small">{{ number }}</small>
      <h3 class="card__content_wrapper__title">{{ title }}</h3>
      <div class="card__content_wrapper__badges">
        <Badge
          :text="type.text"
          :link="type.link"
          v-for="(type, $key) in types"
          :key="$key"
        />
      </div>
    </div>
  </article>
</template>

<script>
import lazyload from "~/plugins/directives/lazyload.client";
export default {
  name: "card",
  props: {
    alternativeText: {
      type: String,
      required: false,
    },
    imagesrc: {
      type: Object,
      required: false,
      default: () => {
        return {
          0: "",
          768: "",
          1024: "",
        };
      },
    },
    number: {
      type: String,
      required: false,
      default: "001",
    },
    title: {
      type: String,
      required: false,
      default: "Pokemon",
    },
    types: {
      type: Array,
      required: false,
      default: () => {
        return [];
      },
    },
  },
  directives: {
    lazyload,
  },
};
</script>
