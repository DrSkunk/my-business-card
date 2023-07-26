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
      label: "QR Code",
      link: "qrcode",
    },
    {
      label: "Info",
      link: "info",
    },
  ];
</script>

<div class="h-full w-full bg-slate-100 flex flex-col md:w-96 mx-auto">
  <img
    class="rounded-full h-36 w-36 mx-auto my-8"
    alt="Sebastiaan Jansen "
    src="/android-chrome-512x512.png"
  />
  <nav class="flex justify-around">
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
