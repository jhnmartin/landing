<script setup>
const crawl = defineProps({
  eventbriteId: String,
});

//grab props from the single and insert into id 3 times
const exampleCallback = () => {
  console.log("Order complete!");
};

const createWidget = () => {
  window.EBWidgets.createWidget({
    widgetType: "checkout",
    eventId: 795728173387,
    modal: true,
    modalTriggerElementId: "eventbrite-widget-modal-trigger-795728173387",
    onOrderComplete: exampleCallback,
  });
};

onMounted(() => {
  const script = document.createElement("script");
  script.src = "https://www.eventbrite.com/static/widgets/eb_widgets.js";
  script.async = true;
  script.onload = () => {
    createWidget();
  };
  document.body.appendChild(script);
});
</script>

<template>
  <div>
    <!-- Noscript content for added SEO -->
    <noscript>
      <a
        href="https://cleveland-halloween-bar-crawl-2023.eventbrite.com"
        rel="noopener noreferrer"
        target="_blank"
        >Buy Tickets on Eventbrite</a
      >
    </noscript>
    <!-- You can customize this button any way you like -->
    <button
      :id="`eventbrite-widget-modal-trigger-795728173387`"
      type="button"
      class="mt-10 flex w-full items-center justify-center rounded-md border border-transparent bg-indigo-600 dark:bg-lime-300 px-8 py-3 text-base font-medium text-white dark:text-zinc-900 hover:bg-indigo-700 dark:hover:bg-lime-200 focus:outline-none focus:ring-2 focus:ring-indigo-500 dark:focus:ring-lime-300 focus:ring-offset-2"
    >
      Buy Tickets
    </button>
  </div>
</template>
