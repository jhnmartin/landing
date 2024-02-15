<script setup lang="ts">
const { data: page } = await useAsyncData("index", () =>
  queryContent("/").findOne()
);

useSeoMeta({
  title: page.value.title,
  ogTitle: page.value.title,
  description: page.value.description,
  ogDescription: page.value.description,
});

defineOgImage({
  component: "Landing",
  title: page.value.title,
  description: page.value.description,
});

const isSunday = ref(false);
</script>

<template>
  <div>
    <ULandingHero
      :title="page.hero.title"
      :description="page.hero.description"
      :links="page.hero.links"
    >
      <template #headline>
        <UBadge
          v-if="page.hero.headline"
          variant="subtle"
          size="lg"
          class="relative rounded-full font-semibold uppercase"
        >
          <NuxtLink
            :to="page.hero.headline.to"
            target="_blank"
            class="focus:outline-none"
            tabindex="-1"
          >
            <span class="absolute inset-0" aria-hidden="true" />
          </NuxtLink>

          {{ page.hero.headline.label }}

          <UIcon
            v-if="page.hero.headline.icon"
            :name="page.hero.headline.icon"
            class="ml-1 w-4 h-4 pointer-events-none"
          />
        </UBadge>
      </template>

      <img
        src="/images/bclxifc.jpg"
        class="w-full h-auto rounded-lg border-2 border-primary-100 dark:border-primary-400"
      />
    </ULandingHero>

    <ULandingSection
      :title="page.features.title"
      :description="page.features.description"
      :headline="page.features.headline"
    >
      <UPageGrid
        id="features"
        class="scroll-mt-[calc(var(--header-height)+140px+128px+96px)]"
      >
        <ULandingCard
          v-for="(item, index) in page.features.items"
          :key="index"
          v-bind="item"
        />
      </UPageGrid>
    </ULandingSection>

    <ULandingSection
      id="pricing"
      :title="page.pricing.title"
      :description="page.pricing.description"
      :headline="page.pricing.headline"
    >
      <ULandingGrid>
        <ULandingCard
          class="col-span-6"
          title="Saturday March 16th"
          description="LIMITED TIME OFFER: Save 20% of general admission tickets with promocode LUCKY20"
          icon="i-heroicons-ticket-solid"
          color="primary"
        >
          <p class="text-4xl font-medium">
            <span class="line-through text-2xl mr-2">$20.00</span>$16.00
          </p>

          <ul class="mb-8">
            <li>☘️ Up To 50% Off Drinks</li>
            <li>☘️ Kick-off, Halftime & After Party</li>
            <li>☘️ Up To 20% Off Select Foods</li>
            <li>☘️ 100s of participants</li>
            <li>☘️ Digital Bar List</li>
            <li>☘️ DJs @ Select Bars</li>
            <li>☘️ Door Cover Charges Waived</li>
            <li>☘️ Free Entry To Top Venues</li>
            <li>☘️ Photographers & or Videographers</li>
            <li>☘️ Tasty Themed Drink Specials</li>
          </ul>
          <EbTicketModal eventbrite-id="795728173387" />
        </ULandingCard>
        <ULandingCard
          class="col-span-6"
          title="Sunday March 17th"
          description="LIMITED TIME OFFER: Save 20% of general admission tickets with promocode LUCKY20"
          icon="i-heroicons-ticket-solid"
          color="primary"
        >
          <p class="text-4xl font-medium">
            <span class="line-through text-2xl mr-2">$20.00</span>$16.00
          </p>

          <ul class="mb-8">
            <li>☘️ Up To 50% Off Drinks</li>
            <li>☘️ Kick-off, Halftime & After Party</li>
            <li>☘️ Up To 20% Off Select Foods</li>
            <li>☘️ 100s of participants</li>
            <li>☘️ Digital Bar List</li>
            <li>☘️ DJs @ Select Bars</li>
            <li>☘️ Door Cover Charges Waived</li>
            <li>☘️ Free Entry To Top Venues</li>
            <li>☘️ Photographers & or Videographers</li>
            <li>☘️ Tasty Themed Drink Specials</li>
          </ul>
          <EbTicketModal eventbrite-id="795737350837" />
        </ULandingCard>
      </ULandingGrid>
    </ULandingSection>

    <!--
      <ULandingSection
      class="bg-primary-50 dark:bg-primary-400 dark:bg-opacity-10"
    >
      <ULandingCTA v-bind="page.cta" :card="false" />
    </ULandingSection>
    -->

    <ULandingSection
      id="faq"
      :title="page.faq.title"
      :description="page.faq.description"
      class="scroll-mt-[var(--header-height)]"
    >
      <ULandingFAQ
        multiple
        :items="page.faq.items"
        :ui="{
          button: {
            label: 'font-semibold',
            trailingIcon: {
              base: 'w-6 h-6',
            },
          },
        }"
        class="max-w-4xl mx-auto"
      />
    </ULandingSection>

    <ULandingSection
      :headline="page.testimonials.headline"
      :title="page.testimonials.title"
      :description="page.testimonials.description"
    >
      <UPageColumns
        id="testimonials"
        class="xl:columns-4 scroll-mt-[calc(var(--header-height)+140px+128px+96px)]"
      >
        <div
          v-for="(testimonial, index) in page.testimonials.items"
          :key="index"
          class="break-inside-avoid"
        >
          <ULandingTestimonial v-bind="testimonial" />
        </div>
      </UPageColumns>
    </ULandingSection>
  </div>
</template>
