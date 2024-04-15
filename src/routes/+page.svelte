<script lang="ts">
  // colors must be defined in the script for Tailwind to register them properly
  let cards = [
    "bg-teal-100",
    "bg-teal-200",
    "bg-teal-300",
    "bg-teal-400",
    "bg-teal-500",
    "bg-teal-600",
  ];

  async function slideCarousel(direction: "left" | "right") {
    const firstCard = cards[0];
    const lastCard = cards[cards.length - 1];

    if (direction === "left") {
      cards = [...cards.slice(1), firstCard];
    } else {
      cards = [lastCard, ...cards.slice(0, -1)];
    }
  }

  const getKey = (card: string, index: number) => `${card}-${index}`;
</script>

<div>
  <div class="carousel absolute grid grid-flow-col gap-10 top-10 w-dvw">
    {#each cards as card, index (getKey(card, index))}
      <div class={`relative h-96 w-64 p-4 ${card}`} />
    {/each}
  </div>

  <div class="absolute top-36">
    <button
      class="text-white p-2 border border-white"
      on:click={() => slideCarousel("left")}>↖</button
    >
    <button
      class="text-white p-2 border border-white"
      on:click={() => slideCarousel("right")}>↘</button
    >
  </div>
</div>

<style>
  .carousel :nth-child(1) {
    top: -18rem;
  }

  .carousel :nth-child(2) {
    top: -12rem;
  }

  .carousel :nth-child(3) {
    top: -6rem;
  }

  .carousel :nth-child(5) {
    top: 6rem;
  }

  .carousel :nth-child(6) {
    top: 12rem;
  }
</style>
