<script lang="ts" context="module">
  function isEmpty(val: string) {
    return val.replace(/\s+/g, '').length === 0;
  }

  function isValidEmail(email: string | null) {
    if (!email || isEmpty(email)) return false;
    const validRegex = /^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/;
    return validRegex.test(email);
  }
</script>

<script lang="ts">
  import { iconArrow, iconError } from '@assets';

  let value = '';
  let state: 'IDLE' | 'ERROR' = 'IDLE';

  function handleSubmit() {
    state = isValidEmail(value) ? 'IDLE' : 'ERROR';
    value = '';
  }

  $: if (value && state === 'ERROR') state = 'IDLE';
</script>

<form class="mt-8" on:submit|preventDefault={handleSubmit}>
  <div class="relative">
    <input
      class="w-full px-6 py-2 | border-2 {state === 'ERROR'
        ? 'border-red-500/70 focus:border-red-500'
        : 'border-red-grayish-700/30 focus:border-red-grayish-700'} rounded-full outline-none placeholder-transparent"
      type="text"
      id="email-address"
      placeholder="john_doe@example.com"
      bind:value />
    <label
      class="absolute bottom-1/2 left-6 transform transition duration-175 translate-y-1/2 text-red-grayish-200/50 pointer-events-none"
      for="email-address">
      Email Address
    </label>

    {#if state === 'ERROR'}
      <span class="absolute top-12 left-6 | text-sm text-red-500">
        Please provide a valid email
      </span>
      <img
        class="absolute right-24 bottom-1/2 transform translate-y-1/2 pointer-events-none"
        src={iconError}
        alt="" />
    {/if}

    <div class="absolute inset-y-0 right-0">
      <button
        class="h-full | px-8 bg-gradient-to-br from-red-500 to-red-300 rounded-full outline-none shadow-lg shadow-red-grayish-200/50 transform scale-110"
        type="submit">
        <span class="sr-only">Submit</span>
        <img src={iconArrow} alt="" />
      </button>
    </div>
  </div>
</form>

<style>
  input:focus + label,
  input:not(:placeholder-shown) + label {
    @apply text-red-grayish-700/70 -translate-y-6;
  }

  button[type='submit']:hover,
  button[type='submit']:focus {
    box-shadow: inset 0 0 100px 100px rgba(255, 255, 255, 0.2);
  }
</style>
