<script setup>
  import { ref } from 'vue'

  const localePath = useLocalePath()
  const detailsElement = ref(null)

  const close = () => {
    detailsElement.value.removeAttribute("open");
  }

  const navigateAndClose = (path) => {
    navigateTo(localePath(path))
    close()
  }

</script>
<template>
  <details
    ref="detailsElement"
    class="z-10 dropdown md:hidden"
  >
    <summary
      tabindex="0"
      class="btn btn-ghost md:hidden p-0"
    >
      <Icon
        name="ion:menu"
        size="32"
      />
    </summary>
    <ul
      tabindex="0"
      class="menu menu-compact dropdown-content"
    >
      <li
        tabindex="0"
        class="rounded-t-box"
      >
        <a @click="navigateAndClose('/courses')">
          {{ $t("courses.title") }}
        </a>
      </li>
      <li>
        <a @click="navigateAndClose('/upload')">
          {{ $t("submit.title") }}
        </a>
      </li>
      <li>
        <a @click="navigateAndClose('/about')">
          {{ $t("about.title") }}
        </a>
      </li>
      <li @click="close()" class="rounded-b-box">
        <UILangSwitcher />
      </li>
    </ul>
  </details>
</template>
<style scoped lang="postcss"> 
  .menu {
    --tw-bg-opacity: 0.8;
    @apply mt-2 p-2 w-60 -ms-[12.5rem];
    @apply rounded-b-box ltr:rounded-br-none rtl:rounded-bl-none border border-base-300 border-t-0;
    @apply shadow bg-base-200;
  }
  ul li {
    @apply bg-base-200;
    --tw-bg-opacity: 0.8;
  }
</style>