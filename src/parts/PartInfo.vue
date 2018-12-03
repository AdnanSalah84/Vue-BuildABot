<template>
  <div>
    <h1>{{ part.title }}</h1>
    <div >
      {{part.description}}
    </div>
  </div>
</template>

<script>
// import parts from '../data/parts';
import getPartsMixin from './get-parts-mixin';

export default {
  name: 'PartInfo',
  mixins: [getPartsMixin],
  // props: ['partType', 'id'],
  props: {
    partType: { type: String },
    id: {
      type: [Number, String], // Either number or string
      validator(value) {
        return Number.isInteger(Number(value));
      },
    },
  },
  computed: {
    part() {
      //   const partType = this.$router.params.partType;
      //   const id = this.$router.params.id;
      // const { partType, id } = this.$route.params;

      const { partType, id } = this; // if props is true in Router index!

      return this.parts[partType].find(part => part.id === +id);
    },
  },

//   props: {
//     partType: { type: String },
//     id: {
//       type: [Number, String],
//       validator(value) {
//         return Number.isInteger(Number(value));
//       },
//     },
//   },
//   computed: {
//     part() {
//       const { partType, id } = this;
//       return parts[partType].find(part => part.id === +id);
//     },
//   },
};
</script>
