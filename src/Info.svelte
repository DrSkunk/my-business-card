<script>
  import data from "./data.js";
  import Discord from "./icons/Discord.svelte";
  import Email from "./icons/Email.svelte";
  import Instagram from "./icons/Instagram.svelte";
  import Twitter from "./icons/Twitter.svelte";
  import Website from "./icons/Website.svelte";
  import QRCode from "qrcode-svg";

  const info = [
    {
      icon: Instagram,
      label: "Instagram",
      value: data.instagram,
      link: `https://www.instagram.com/${data.instagram}/`,
    },
    {
      icon: Twitter,
      label: "Twitter",
      value: data.twitter,
      link: `https://twitter.com/${data.twitter}`,
    },
    {
      icon: Email,
      label: "Email",
      value: data.email,
      link: `mailto:${data.email}`,
    },
    {
      icon: Website,
      label: "Website",
      value: data.website,
      link: data.website,
    },
    {
      icon: Discord,
      label: "Discord",
      value: data.discord,
      link: "https://discordapp.com/users/185089816218697729",
    },
  ];

  let selectedItem = null;
  let svg = null;

  function showQRCode(item) {
    selectedItem = item;
    svg = new QRCode({
      content: item.link,
      ecl: "L",
    }).svg();
    console.log(svg);
  }
</script>

<div class="flex flex-col gap-4 p-4">
  {#if svg}
    <div class="flex flex-col items-center gap-2">
      <button
        on:click={() => {
          selectedItem = null;
          svg = null;
        }}>{@html svg}</button
      >
      <a
        href={selectedItem.link}
        class="text-2xl font-thin hover:text-slate-500"
      >
        {selectedItem.label}
      </a>
    </div>
  {:else}
    {#each info as item}
      <div class="flex items-center gap-2">
        <button
          class="text-slate-900 hover:text-slate-500 inline-flex items-center"
          on:click={() => showQRCode(item)}
        >
          <div class="h-12 w-12 p-2 mr-2 bg-black rounded-full text-white">
            <svelte:component this={item.icon} />
          </div>
          {item.value}
        </button>
      </div>
    {/each}
  {/if}
</div>
