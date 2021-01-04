<template>
  <section class="home">
    <div class="py-24 md:py-36 mx-auto flex flex-wrap flex-col md:flex-row items-center">
      <div class="flex flex-col w-full xl:w-3/5 justify-center lg:items-start overflow-y-hidden">
        <div v-html="$md.render(welcomeText)" class="home__welcome markdown" />

        <div class="mb-12 xl:mb-0">
          <div class="form-group">
            <input
              ref="emailInput"
              v-model="form.email"
              class="form-control"
              type="text"
              name="email"
              placeholder="your@email.com"
              aria-label="Email address"
            />
          </div>
          <div class="form-group">
            <input
              id="password"
              v-model="form.password"
              type="password"
              class="form-control"
              placeholder="password"
              aria-label="Password"
            />
          </div>

          <a href="/blog">
            <button
              type="button"
              class="btn btn-primary btn-block mt-4"
              :disable="form.email === '' || form.password === ''"
            >
              ログイン
            </button>
          </a>
        </div>
      </div>
      <div class="flex flex-col w-full xl:w-2/5">
        <img
          alt="Hero"
          class="rounded shadow-xl"
          src="https://source.unsplash.com/random/720x400"
        />
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator';
import settings from '@/content/settings/general.json';

@Component({
  // Called to know which transition to apply
  transition() {
    return 'slide-left';
  },
})
export default class Home extends Vue {
  welcomeText = settings.welcomeText;

  get posts(): Post[] {
    return this.$store.state.posts;
  }

  form = {
    email: '',
    password: '',
  };
}
</script>
