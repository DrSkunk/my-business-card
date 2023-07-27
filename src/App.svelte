<script>
  import Info from "./Info.svelte";
  import QRCode from "./QRCode.svelte";

  let page = "info";
  const pageComponent = {
    info: Info,
    qrcode: QRCode,
  };

  const items = [
    {
      label: "Info",
      link: "info",
    },
    {
      label: "vCard",
      link: "qrcode",
    },
  ];
</script>

<div
  class="font-extralight h-full w-full bg-slate-100 flex flex-col md:w-96 mx-auto items-center"
>
  <img
    class="rounded-full h-36 w-36 mx-auto mt-8 mb-2 drop-shadow-lg"
    alt="Sebastiaan Jansen "
    src="/me.jpg"
  />
  <h1 class="text-3xl font-thin mb-2">Sebastiaan Jansen</h1>
  <h2 class="mb-4">Maker of things</h2>
  <nav class="flex justify-around gap-4 mb-2">
    {#each items as item}
      <button
        class="bg-white px-4 py-2 border-b-2 transition-all w-36"
        class:border-slate-500={page === item.link}
        class:border-transparent={page !== item.link}
        on:click={() => (page = item.link)}>{item.label}</button
      >
    {/each}
  </nav>
  <svelte:component this={pageComponent[page]} />
</div>
