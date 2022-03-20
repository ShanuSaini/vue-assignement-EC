<template>
  <div
    class="advanced-search-wrapper"
    :class="{ 'advanced-options-visible': isAdvancedMode }"
  >
    <h1>Search</h1>
    <div class="search-wrapper">
      <label class="input-label">KEYWORD</label>
      <div class="search-field-wrapper">
        <TextInput v-model="searchText" />
        <SearchButton buttonText="SEARCH" @buttonClicked="search" />
      </div>
      <ToggleInput label="Advanced mode" v-model="isAdvancedMode" />
    </div>

    <AdvanceSearchOptions
      :class="{ visible: isAdvancedMode }"
      @change="advancedOptionsChanged"
    />
  </div>
</template>

<script>
import TextInput from '@/components/inputs/TextInput.vue';
import ToggleInput from '@/components/inputs/ToggleInput.vue';
import SearchButton from '@/components/SearchButton.vue';
import AdvanceSearchOptions from '@/components/AdvanceSearchOptions.vue';

export default {
  name: 'SearchWrapper',
  components: {
    SearchButton,
    TextInput,
    ToggleInput,
    AdvanceSearchOptions
  },
  data() {
    return {
      searchText: '',
      isAdvancedMode: false,
      selectedCountry: '',
      selectedType: ''
    };
  },
  methods: {
    advancedOptionsChanged(data) {
      this.selectedCountry = data.country;
      this.selectedType = data.type;
    },
    search() {
      const advancedSearchValues = `Values: Country = ${this.selectedCountry}, Type = ${this.selectedType}`;
      const alertString = `Searching Term = ${this.searchText}, ${
        this.isAdvancedMode ? 'With' : 'Without'
      } Advanced Search Option ${
        this.isAdvancedMode ? advancedSearchValues : ''
      }`;
      alert(alertString);
    }
  }
};
</script>

<style scoped lang="scss">
h1 {
  line-height: 35px;
  font-size: 28px;
  color: #ffffff;
  text-align: center;
  margin-bottom: 20px;
  font-weight: bold;
}
.search-field-wrapper {
  margin-bottom: 10px;
  display: flex;
}
.advanced-search-wrapper {
  width: 100%;
  max-width: 540px;
  margin: auto;
  will-change: transform;
  transform: translateY(50px);
  transition: transform 0.3s;
  &.advanced-options-visible {
    transform: translateY(0);
  }
}
.search-wrapper {
  padding: 20px;
  background-color: #fff;
  margin-bottom: 10px;
  border-radius: 3px;
}
</style>
