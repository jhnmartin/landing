<script setup lang="ts">
const links = [
  {
    label: "Resources",
    children: [
      {
        label: "Help center",
      },
      {
        label: "Docs",
      },
      {
        label: "Roadmap",
      },
      {
        label: "Changelog",
      },
    ],
  },
  {
    label: "Features",
    children: [
      {
        label: "Affiliates",
      },
      {
        label: "Portal",
      },
      {
        label: "Jobs",
      },
      {
        label: "Sponsors",
      },
    ],
  },
  {
    label: "Company",
    children: [
      {
        label: "About",
      },
      {
        label: "Pricing",
      },
      {
        label: "Careers",
      },
      {
        label: "Blog",
      },
    ],
  },
];

const toast = useToast();

const email = ref("");
const loading = ref(false);

function onSubmit() {
  loading.value = true;

  setTimeout(() => {
    toast.add({
      title: "Subscribed!",
      description: "You've been subscribed to our newsletter.",
    });

    loading.value = false;
  }, 1000);
}
</script>

<template>
  <UFooter>
    <template #left>
      <p class="text-gray-500 dark:text-gray-400 text-sm">
        Copyright © {{ new Date().getFullYear() }}. All rights reserved.
      </p>
    </template>

    <template #right>
      <UColorModeButton size="sm" />

      <UButton
        to="https://www.instagram.com/barcrawllive/"
        target="_blank"
        icon="i-simple-icons-instagram"
        aria-label="GitHub"
        color="gray"
        variant="ghost"
      />
    </template>
  </UFooter>
</template>
