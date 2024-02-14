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
    eventId: crawl.eventbriteId,
    modal: true,
    modalTriggerElementId: `eventbrite-widget-modal-trigger-${crawl.eventbriteId}`,
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
    <UButton :id="`eventbrite-widget-modal-trigger-${crawl.eventbriteId}`">
      Buy Tickets
    </UButton>
  </div>
</template>
