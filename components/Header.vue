<script setup lang="ts">
const nuxtApp = useNuxtApp();
const { activeHeadings, updateHeadings } = useScrollspy();

const links = computed(() => [
  {
    label: "Features",
    to: "#features",
    icon: "i-heroicons-cube-transparent",
    active:
      activeHeadings.value.includes("features") &&
      !activeHeadings.value.includes("pricing"),
  },
  {
    label: "Get Tickets",
    to: "#pricing",
    icon: "i-heroicons-credit-card",
    active:
      activeHeadings.value.includes("pricing") &&
      !activeHeadings.value.includes("testimonials"),
  },
  {
    label: "FAQ",
    to: "#faq",
    icon: "i-heroicons-question-mark-circle",
    active: activeHeadings.value.includes("faq"),
  },
  {
    label: "Testimonials",
    to: "#testimonials",
    icon: "i-heroicons-academic-cap",
    active: activeHeadings.value.includes("testimonials"),
  },
]);

nuxtApp.hooks.hookOnce("page:finish", () => {
  updateHeadings([
    document.querySelector("#features"),
    document.querySelector("#pricing"),
    document.querySelector("#faq"),
    document.querySelector("#testimonials"),
  ]);
});
</script>

<template>
  <UHeader :links="links">
    <template #logo> BCL X IFC </template>

    <template #right>
      <UButton
        label="Visit Bar Crawl LIVE!"
        color="white"
        variant="ghost"
        trailing-icon="i-heroicons-arrow-right-20-solid"
        class="hidden lg:flex"
        to="https://barcrawllive.com"
      />
    </template>

    <template #panel>
      <UAsideLinks :links="links" />

      <UDivider class="my-6" />

      <UButton label="GET TICKETS" block class="mb-3" to="#pricing" />
      <UButton
        label="Bar Crawl LIVE!"
        color="white"
        block
        to="https://www.barcrawllive.com/"
        target="_blank"
      />
    </template>
  </UHeader>
</template>
