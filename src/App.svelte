<script lang="ts">
  import { Form } from '@layout';
  import { heroDesktop, heroMobile, logo } from '@assets';
</script>

<header class="fixed top-0 inset-x-0 h-22 | bg-white xl:hidden">
  <div class="h-full max-w-xs mx-auto | flex items-center sm:justify-center">
    <img src={logo} alt="Base Apparel" />
  </div>
</header>

<main class="py-22 | xl:py-0">
  <section class="h-full grid gap-18 xl:(grid-cols-2 items-center gap-6)">
    <picture class="xl:order-2" aria-hidden="true">
      <source media="(min-width: 376px)" srcset={heroDesktop} />
      <img class="max-h-screen h-full w-full | object-cover object-top" src={heroMobile} alt="" />
    </picture>
    <div
      class="max-w-xs mx-auto | flex flex-col gap-3 | text-center | md:(max-w-lg gap-12) xl:text-left">
      <img class="mb-14 hidden xl:block" src={logo} alt="Base Apparel" width="125" />
      <h1 class="text-5xl uppercase tracking-0.15em | @sm:text-6xl @md:text-8xl lg:text-6xl">
        <span class="text-red-grayish-200 font-light"> We're </span> <br />
        <span class="text-red-grayish-700"> coming soon </span>
      </h1>
      <p class="text-red-grayish-200 leadint-relaxed @sm:text-2xl @md:text-3xl lg:text-xl">
        Hello fellow shoppers! We're currently building our new fashion store. Add your email below
        to stay up-to-date with announcements and our launch deals.
      </p>
      <Form />
    </div>
  </section>
</main>
