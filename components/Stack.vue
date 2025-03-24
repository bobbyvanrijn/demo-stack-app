<script setup>
import { computed } from 'vue';

const props = defineProps({
    element: {
        type: String,
        default: 'div'
    },
  // Main flexbox direction
  direction: {
    type: String,
    default: 'vertical',
    validator: (value) => ['vertical', 'horizontal'].includes(value)
  },
  // Direction at different breakpoints
  directionSm: {
    type: String,
    default: null,
    validator: (value) => value === null || ['vertical', 'horizontal'].includes(value)
  },
  directionMd: {
    type: String,
    default: null,
    validator: (value) => value === null || ['vertical', 'horizontal'].includes(value)
  },
  directionLg: {
    type: String,
    default: null,
    validator: (value) => value === null || ['vertical', 'horizontal'].includes(value)
  },
  // Space between items
  spacing: {
    type: String,
    default: 'none',
    validator: (value) => ['none', 'xs', 'sm', 'md', 'lg', 'xl', 'xxl', 'custom'].includes(value)
  },
  // Spacing at different breakpoints
  spacingSm: {
    type: String,
    default: null,
    validator: (value) => value === null || ['none', 'xs', 'sm', 'md', 'lg', 'xl', 'xxl', 'custom'].includes(value)
  },
  spacingMd: {
    type: String,
    default: null,
    validator: (value) => value === null || ['none', 'xs', 'sm', 'md', 'lg', 'xl', 'xxl', 'custom'].includes(value)
  },
  spacingLg: {
    type: String,
    default: null,
    validator: (value) => value === null || ['none', 'xs', 'sm', 'md', 'lg', 'xl', 'xxl', 'custom'].includes(value)
  },
  // Custom spacing value (when spacing is 'custom')
  customSpacing: {
    type: String,
    default: '0'
  },
  // Alignment along the cross axis
  align: {
    type: String,
    default: 'stretch',
    validator: (value) => ['start', 'end', 'center', 'stretch', 'baseline'].includes(value)
  },
  // Alignment at different breakpoints
  alignSm: {
    type: String,
    default: null,
    validator: (value) => value === null || ['start', 'end', 'center', 'stretch', 'baseline'].includes(value)
  },
  alignMd: {
    type: String,
    default: null,
    validator: (value) => value === null || ['start', 'end', 'center', 'stretch', 'baseline'].includes(value)
  },
  alignLg: {
    type: String,
    default: null,
    validator: (value) => value === null || ['start', 'end', 'center', 'stretch', 'baseline'].includes(value)
  },
  // Alignment along the main axis
  justify: {
    type: String,
    default: 'start',
    validator: (value) => ['start', 'end', 'center', 'between', 'around', 'evenly'].includes(value)
  },
  // Justify at different breakpoints
  justifySm: {
    type: String,
    default: null,
    validator: (value) => value === null || ['start', 'end', 'center', 'between', 'around', 'evenly'].includes(value)
  },
  justifyMd: {
    type: String,
    default: null,
    validator: (value) => value === null || ['start', 'end', 'center', 'between', 'around', 'evenly'].includes(value)
  },
  justifyLg: {
    type: String,
    default: null,
    validator: (value) => value === null || ['start', 'end', 'center', 'between', 'around', 'evenly'].includes(value)
  },
  // Whether items should wrap
  wrap: {
    type: Boolean,
    default: false
  },
  // Wrap at different breakpoints
  wrapSm: {
    type: Boolean,
    default: null
  },
  wrapMd: {
    type: Boolean,
    default: null
  },
  wrapLg: {
    type: Boolean,
    default: null
  },
  // Row gap for wrapped items
  rowGap: {
    type: String,
    default: 'none',
    validator: (value) => ['none', 'xs', 'sm', 'md', 'lg', 'xl', 'xxl', 'custom'].includes(value)
  },
  // Custom row gap value (when rowGap is 'custom')
  customRowGap: {
    type: String,
    default: '0'
  },
  // Whether to fill the container width
  fullWidth: {
    type: Boolean,
    default: false
  },
  // Whether to fill the container height
  fullHeight: {
    type: Boolean,
    default: false
  }
});

const stackClasses = computed(() => {
  const classes = ['stack'];
  
  // Direction modifier
  classes.push(`stack--${props.direction}`);
  
  // Breakpoint-specific direction modifiers
  if (props.directionSm) classes.push(`stack--sm-${props.directionSm}`);
  if (props.directionMd) classes.push(`stack--md-${props.directionMd}`);
  if (props.directionLg) classes.push(`stack--lg-${props.directionLg}`);
  
  // Spacing modifier
  if (props.spacing !== 'none') {
    if (props.spacing === 'custom') {
      classes.push('stack--spacing-custom');
    } else {
      classes.push(`stack--spacing-${props.spacing}`);
    }
  }
  
  // Breakpoint-specific spacing modifiers
  if (props.spacingSm) {
    if (props.spacingSm === 'custom') {
      classes.push('stack--sm-spacing-custom');
    } else {
      classes.push(`stack--sm-spacing-${props.spacingSm}`);
    }
  }
  
  if (props.spacingMd) {
    if (props.spacingMd === 'custom') {
      classes.push('stack--md-spacing-custom');
    } else {
      classes.push(`stack--md-spacing-${props.spacingMd}`);
    }
  }
  
  if (props.spacingLg) {
    if (props.spacingLg === 'custom') {
      classes.push('stack--lg-spacing-custom');
    } else {
      classes.push(`stack--lg-spacing-${props.spacingLg}`);
    }
  }
  
  // Align modifier
  if (props.align !== 'stretch') {
    classes.push(`stack--align-${props.align}`);
  }
  
  // Breakpoint-specific align modifiers
  if (props.alignSm) classes.push(`stack--sm-align-${props.alignSm}`);
  if (props.alignMd) classes.push(`stack--md-align-${props.alignMd}`);
  if (props.alignLg) classes.push(`stack--lg-align-${props.alignLg}`);
  
  // Justify modifier
  if (props.justify !== 'start') {
    classes.push(`stack--justify-${props.justify}`);
  }
  
  // Breakpoint-specific justify modifiers
  if (props.justifySm) classes.push(`stack--sm-justify-${props.justifySm}`);
  if (props.justifyMd) classes.push(`stack--md-justify-${props.justifyMd}`);
  if (props.justifyLg) classes.push(`stack--lg-justify-${props.justifyLg}`);
  
  // Wrap modifier
  if (props.wrap) {
    classes.push('stack--wrap');
  }
  
  // Breakpoint-specific wrap modifiers
  if (props.wrapSm !== null) classes.push(props.wrapSm ? 'stack--sm-wrap' : 'stack--sm-nowrap');
  if (props.wrapMd !== null) classes.push(props.wrapMd ? 'stack--md-wrap' : 'stack--md-nowrap');
  if (props.wrapLg !== null) classes.push(props.wrapLg ? 'stack--lg-wrap' : 'stack--lg-nowrap');
  
  // Row gap modifier
  if (props.rowGap !== 'none') {
    if (props.rowGap === 'custom') {
      classes.push('stack--row-gap-custom');
    } else {
      classes.push(`stack--row-gap-${props.rowGap}`);
    }
  }
  
  // Full width modifier
  if (props.fullWidth) {
    classes.push('stack--full-width');
  }
  
  // Full height modifier
  if (props.fullHeight) {
    classes.push('stack--full-height');
  }
  
  return classes.join(' ');
});

const stackStyles = computed(() => {
  const styles = {};
  
  // Apply custom spacing if specified
  if (props.spacing === 'custom') {
    styles['--stack-custom-spacing'] = props.customSpacing;
  }
  
  // Apply custom row gap if specified
  if (props.rowGap === 'custom') {
    styles['--stack-custom-row-gap'] = props.customRowGap;
  }
  
  return styles;
});
</script>

<template>
  <component
    :is="element"
    :class="stackClasses"
    :style="stackStyles"
    :attrs="$attrs"
>
    <slot></slot>
  </component>
</template>

<style>
:root {
  /* Default spacing variables that can be overridden at the site level */
  --stack-spacing-xs: 4px;
  --stack-spacing-sm: 8px;
  --stack-spacing-md: 16px;
  --stack-spacing-lg: 24px;
  --stack-spacing-xl: 32px;
  --stack-spacing-xxl: 48px;
  
  /* Breakpoints */
  --stack-breakpoint-sm: 576px;
  --stack-breakpoint-md: 768px;
  --stack-breakpoint-lg: 992px;
}

/* Base Stack Block */
.stack {
  display: flex;
}

/* Direction Modifiers */
.stack--vertical {
  flex-direction: column;
}

.stack--horizontal {
  flex-direction: row;
}

/* Spacing Modifiers */
.stack--spacing-xs {
  gap: var(--stack-spacing-xs);
}

.stack--spacing-sm {
  gap: var(--stack-spacing-sm);
}

.stack--spacing-md {
  gap: var(--stack-spacing-md);
}

.stack--spacing-lg {
  gap: var(--stack-spacing-lg);
}

.stack--spacing-xl {
  gap: var(--stack-spacing-xl);
}

.stack--spacing-xxl {
  gap: var(--stack-spacing-xxl);
}

.stack--spacing-custom {
  gap: var(--stack-custom-spacing);
}

/* Align Modifiers */
.stack--align-start {
  align-items: flex-start;
}

.stack--align-end {
  align-items: flex-end;
}

.stack--align-center {
  align-items: center;
}

.stack--align-baseline {
  align-items: baseline;
}

.stack--align-stretch {
  align-items: stretch;
}

/* Justify Modifiers */
.stack--justify-start {
  justify-content: flex-start;
}

.stack--justify-end {
  justify-content: flex-end;
}

.stack--justify-center {
  justify-content: center;
}

.stack--justify-between {
  justify-content: space-between;
}

.stack--justify-around {
  justify-content: space-around;
}

.stack--justify-evenly {
  justify-content: space-evenly;
}

/* Wrap Modifier */
.stack--wrap {
  flex-wrap: wrap;
}

.stack--nowrap {
  flex-wrap: nowrap;
}

/* Row Gap Modifiers */
.stack--row-gap-xs {
  row-gap: var(--stack-spacing-xs);
}

.stack--row-gap-sm {
  row-gap: var(--stack-spacing-sm);
}

.stack--row-gap-md {
  row-gap: var(--stack-spacing-md);
}

.stack--row-gap-lg {
  row-gap: var(--stack-spacing-lg);
}

.stack--row-gap-xl {
  row-gap: var(--stack-spacing-xl);
}

.stack--row-gap-xxl {
  row-gap: var(--stack-spacing-xxl);
}

.stack--row-gap-custom {
  row-gap: var(--stack-custom-row-gap);
}

/* Full Width Modifier */
.stack--full-width {
  width: 100%;
}

/* Full Height Modifier */
.stack--full-height {
  height: 100%;
}

/* Small Breakpoint (sm) */
@media (min-width: 576px) {
  /* Direction modifiers */
  .stack--sm-vertical {
    flex-direction: column;
  }
  
  .stack--sm-horizontal {
    flex-direction: row;
  }
  
  /* Spacing modifiers */
  .stack--sm-spacing-xs {
    gap: var(--stack-spacing-xs);
  }
  
  .stack--sm-spacing-sm {
    gap: var(--stack-spacing-sm);
  }
  
  .stack--sm-spacing-md {
    gap: var(--stack-spacing-md);
  }
  
  .stack--sm-spacing-lg {
    gap: var(--stack-spacing-lg);
  }
  
  .stack--sm-spacing-xl {
    gap: var(--stack-spacing-xl);
  }
  
  .stack--sm-spacing-xxl {
    gap: var(--stack-spacing-xxl);
  }
  
  /* Align modifiers */
  .stack--sm-align-start {
    align-items: flex-start;
  }
  
  .stack--sm-align-end {
    align-items: flex-end;
  }
  
  .stack--sm-align-center {
    align-items: center;
  }
  
  .stack--sm-align-baseline {
    align-items: baseline;
  }
  
  .stack--sm-align-stretch {
    align-items: stretch;
  }
  
  /* Justify modifiers */
  .stack--sm-justify-start {
    justify-content: flex-start;
  }
  
  .stack--sm-justify-end {
    justify-content: flex-end;
  }
  
  .stack--sm-justify-center {
    justify-content: center;
  }
  
  .stack--sm-justify-between {
    justify-content: space-between;
  }
  
  .stack--sm-justify-around {
    justify-content: space-around;
  }
  
  .stack--sm-justify-evenly {
    justify-content: space-evenly;
  }
  
  /* Wrap modifiers */
  .stack--sm-wrap {
    flex-wrap: wrap;
  }
  
  .stack--sm-nowrap {
    flex-wrap: nowrap;
  }
}

/* Medium Breakpoint (md) */
@media (min-width: 768px) {
  /* Direction modifiers */
  .stack--md-vertical {
    flex-direction: column;
  }
  
  .stack--md-horizontal {
    flex-direction: row;
  }
  
  /* Spacing modifiers */
  .stack--md-spacing-xs {
    gap: var(--stack-spacing-xs);
  }
  
  .stack--md-spacing-sm {
    gap: var(--stack-spacing-sm);
  }
  
  .stack--md-spacing-md {
    gap: var(--stack-spacing-md);
  }
  
  .stack--md-spacing-lg {
    gap: var(--stack-spacing-lg);
  }
  
  .stack--md-spacing-xl {
    gap: var(--stack-spacing-xl);
  }
  
  .stack--md-spacing-xxl {
    gap: var(--stack-spacing-xxl);
  }
  
  /* Align modifiers */
  .stack--md-align-start {
    align-items: flex-start;
  }
  
  .stack--md-align-end {
    align-items: flex-end;
  }
  
  .stack--md-align-center {
    align-items: center;
  }
  
  .stack--md-align-baseline {
    align-items: baseline;
  }
  
  .stack--md-align-stretch {
    align-items: stretch;
  }
  
  /* Justify modifiers */
  .stack--md-justify-start {
    justify-content: flex-start;
  }
  
  .stack--md-justify-end {
    justify-content: flex-end;
  }
  
  .stack--md-justify-center {
    justify-content: center;
  }
  
  .stack--md-justify-between {
    justify-content: space-between;
  }
  
  .stack--md-justify-around {
    justify-content: space-around;
  }
  
  .stack--md-justify-evenly {
    justify-content: space-evenly;
  }
  
  /* Wrap modifiers */
  .stack--md-wrap {
    flex-wrap: wrap;
  }
  
  .stack--md-nowrap {
    flex-wrap: nowrap;
  }
}

/* Large Breakpoint (lg) */
@media (min-width: 992px) {
  /* Direction modifiers */
  .stack--lg-vertical {
    flex-direction: column;
  }
  
  .stack--lg-horizontal {
    flex-direction: row;
  }
  
  /* Spacing modifiers */
  .stack--lg-spacing-xs {
    gap: var(--stack-spacing-xs);
  }
  
  .stack--lg-spacing-sm {
    gap: var(--stack-spacing-sm);
  }
  
  .stack--lg-spacing-md {
    gap: var(--stack-spacing-md);
  }
  
  .stack--lg-spacing-lg {
    gap: var(--stack-spacing-lg);
  }
  
  .stack--lg-spacing-xl {
    gap: var(--stack-spacing-xl);
  }
  
  .stack--lg-spacing-xxl {
    gap: var(--stack-spacing-xxl);
  }
  
  /* Align modifiers */
  .stack--lg-align-start {
    align-items: flex-start;
  }
  
  .stack--lg-align-end {
    align-items: flex-end;
  }
  
  .stack--lg-align-center {
    align-items: center;
  }
  
  .stack--lg-align-baseline {
    align-items: baseline;
  }
  
  .stack--lg-align-stretch {
    align-items: stretch;
  }
  
  /* Justify modifiers */
  .stack--lg-justify-start {
    justify-content: flex-start;
  }
  
  .stack--lg-justify-end {
    justify-content: flex-end;
  }
  
  .stack--lg-justify-center {
    justify-content: center;
  }
  
  .stack--lg-justify-between {
    justify-content: space-between;
  }
  
  .stack--lg-justify-around {
    justify-content: space-around;
  }
  
  .stack--lg-justify-evenly {
    justify-content: space-evenly;
  }
  
  /* Wrap modifiers */
  .stack--lg-wrap {
    flex-wrap: wrap;
  }
  
  .stack--lg-nowrap {
    flex-wrap: nowrap;
  }
}

/* Clear all common typography spacing 
    with an easily overridable CSS layer
*/
@layer stack {
    h1, h2, h3, h4, h5, h6, p, ul, ol, dl, blockquote, pre, address, hr, figure, table, fieldset {
        margin-top: 0;
        margin-bottom: 0;
    }
}
</style>