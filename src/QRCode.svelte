<script>
  import QRCode from "qrcode-svg";
  import data from "./data.js";
  //   import QRCode from "qrcode";

  const vcard = `BEGIN:VCARD
VERSION:4.0
FN:${data.name} ${data.surname} (Wintergatan)
N:${data.surname} (Wintergatan);${data.name};;;
NICKNAME:${data.nickname}
EMAIL;type=WORK;type=pref:${data.email}
X-SOCIALPROFILE;TYPE=twitter:https://twitter.com/${data.twitter}
X-SOCIALPROFILE;TYPE=instagram:https://www.instagram.com/${data.instagram}/
X-SOCIALPROFILE;TYPE=Discord:${data.discord}
URL:${data.website}
END:VCARD`;

  const svg = new QRCode({
    content: vcard,
    ecl: "L",
  }).svg();
</script>

<div class="mx-auto pt-4">
  {@html svg}
</div>
<!-- <img class="aspect-square w-full" src={imgSrc} alt="QR Code" /> -->
