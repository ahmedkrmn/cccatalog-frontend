<template>
  <div class="hero">
    <img class="logo" src="../assets/cc-logo_large_black.png">
    <div class="hero_search-form search-form_ctr">
      <search-grid-form></search-grid-form>
    </div>
    <div class="description">
        <p>
          Search for free content in the public domain and under Creative Commons licenses.
          <br />
          Learn more about CC licenses <a href="https://creativecommons.org/share-your-work/licensing-types-examples/">here</a>.
        </p>
    </div>
    <div class="old-search-link">
      <span>
        Looking for the old CC Search portal? Go
        <a href="https://oldsearch.creativecommons.org/">here</a>
      </span>
    </div>
  </div>
</template>

<script>
import { SET_QUERY } from '@/store/mutation-types';
import SearchGridForm from '@/components/SearchGridForm';

export default {
  name: 'hero-section',
  components: {
    SearchGridForm,
  },
  data: () => ({ form: { searchTerm: '' } }),
  methods: {
    onSubmit() {
      this.$store.commit(SET_QUERY, { query: { q: this.form.searchTerm }, shouldNavigate: true });
    },
  },
};
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import '../../node_modules/foundation-sites/scss/foundation';

$hero-height: 75vh;

.hero {
  background: #e9ebee;
  position: relative;
  height: $hero-height;
  background-size: cover;
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  min-height: 300px;

  .logo {
    margin-bottom: 4vh;
    height: 7em;

    @media screen and (max-width: 39.9375em) {
      height: 5.5em;
    }
  }

  .hero_search-form {
    position: relative;
    margin-top: 0;
    border-radius: 3px;
    max-width: 580px;
    width: 100%;
  }

  &:before {
    content: '';
    position: absolute;
    background: linear-gradient(to top,
                rgba(0, 0, 0, 0.1) 0%,
                rgba(17, 17, 17, 0.7) 100%);
  }
}

.description {
  margin-top: 2vh;
  font-style: italic;
}

.old-search-link {
  position: absolute;
  top: 2rem;
  right: 2rem;

  @media screen and (max-width: 320px) {
    top: 0;
    font-size: 0.9rem;
  }
}

/* Small only */
@media screen and (max-width: 40em) {
  .hero {
    height: 60vh;
  }
  .search-form_ctr {
    padding: 0 .9375rem;
  }
  .logo {
    height: 5.5em;
  }
}
</style>
<style src="vue-multiselect/dist/vue-multiselect.min.css"></style>

<style lang="scss">
#app .search-form_input::placeholder {
  color: rgb(130, 130, 130);
}

#app .search-form_search-button{
  margin-left:auto; margin-right:0;
}

/* Small only */
@media screen and (max-width: 40em) {
  #app .search-form_input {
    font-size: 20px;
    padding-left: 15px;
  }
  #app .search-form_search-button {
    right: 10px;
  }
}
</style>