<template>
  <li :class="`cv-toolbar-title ${carbonPrefix}--toolbar-menu__title`">{{ title }}</li>
</template>

<script>
import carbonPrefixMixin from '../../mixins/carbon-prefix-mixin';
export default {
  name: 'CvToolbarTitle',
  mixins: [carbonPrefixMixin],
  props: {
    title: { type: String, required: true },
  },
};
</script>
