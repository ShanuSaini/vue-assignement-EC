<template>
  <div class="advance-search-options-wrapper">
    <div class="row">
      <div class="col">
        <SelectInput label="COUNTRY" :items="countries" v-model="country" />
      </div>
      <div class="col">
        <SelectInput label="TYPE" :items="types" v-model="type" />
      </div>
    </div>
  </div>
</template>

<script>
import SelectInput from '@/components/inputs/SelectInput.vue';

export default {
  name: 'AdvanceSearchOptions',
  components: {
    SelectInput
  },
  data() {
    return {
      countries: [
        {
          text: 'United States',
          value: 'US'
        },
        {
          text: 'Canada',
          value: 'CA'
        },
        {
          text: 'Poland',
          value: 'PL'
        }
      ],
      types: [
        {
          text: 'Poems',
          value: 'Poems'
        },
        {
          text: 'Articles',
          value: 'Articles'
        },
        {
          text: 'Novels',
          value: 'Novels'
        }
      ],
      country: '',
      type: ''
    };
  },
  watch: {
    country() {
      this.emitValueChange();
    },
    type() {
      this.emitValueChange();
    }
  },
  methods: {
    emitValueChange() {
      this.$emit('change', {
        country: this.country,
        type: this.type
      });
    }
  }
};
</script>

<style scoped lang="scss">
.advance-search-options-wrapper {
  background-color: #fff;
  opacity: 0;
  transition: opacity 0.3s;
  will-change: opacity;
  padding: 20px;
  border-radius: 3px;
  &.visible {
    opacity: 1;
  }
}
.row {
  display: flex;
  justify-content: space-between;
}
.col {
  width: calc(50% - 5px);
}
</style>
