<script>
  import data from "./data.js";
  import Discord from "./icons/Discord.svelte";
  import Email from "./icons/Email.svelte";
  import Instagram from "./icons/Instagram.svelte";
  import Twitter from "./icons/Twitter.svelte";
  import Website from "./icons/Website.svelte";
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
</script>

<div class="flex flex-col gap-4 p-4">
  {#each info as entry}
    <div class="flex items-center gap-2">
      <a
        class="text-slate-900 hover:text-slate-500 inline-flex items-center"
        href={entry.link}
        target="_blank"
      >
        <div class="h-12 w-12 p-2 mr-2 bg-black rounded-full text-white">
          <svelte:component this={entry.icon} />
        </div>
        {entry.value}</a
      >
    </div>
  {/each}
</div>
