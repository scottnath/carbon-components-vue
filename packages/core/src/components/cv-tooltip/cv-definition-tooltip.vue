<template>
  <div :class="`cv-definition-tooltip ${carbonPrefix}--tooltip--definition ${carbonPrefix}--tooltip--a11y`">
    <button
      :aria-describedby="`${uid}-label`"
      :class="[
        `${carbonPrefix}--tooltip__trigger`,
        `${carbonPrefix}--tooltip--a11y`,
        `${carbonPrefix}--tooltip__trigger--definition`,
        `${carbonPrefix}--tooltip--${direction}`,
        `${carbonPrefix}--tooltip--align-${alignment}`,
      ]"
      type="button"
    >
      {{ term }}
    </button>
    <div :class="`${carbonPrefix}--assistive-text`" :id="`${uid}-label`" role="tooltip">{{ definition }}</div>
  </div>
</template>

<script>
import uidMixin from '../../mixins/uid-mixin';
import carbonPrefixMixin from '../../mixins/carbon-prefix-mixin';

export default {
  name: 'CvDefinitionTooltip',
  mixins: [uidMixin, carbonPrefixMixin],
  props: {
    alignment: { type: String, default: 'center', validator: val => ['start', 'center', 'end'].includes(val) },
    definition: { type: String, required: true },
    direction: {
      type: String,
      default: 'top',
      validator(val) {
        const validValues = ['top', 'bottom'];
        const valid = validValues.includes(val);
        if (!valid) {
          console.warn(`CVDefinitionTooltip.direction must be one of the following: ${validValues}`);
        }
        return valid;
      },
    },
    term: { type: String, required: true },
  },
};
</script>
