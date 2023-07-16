```js
// Remember to install mini-svg-data-uri
// Follow me on twitter for memes @jordienr

import { type Config } from "tailwindcss";
const {
  default: flattenColorPalette,
} = require("tailwindcss/lib/util/flattenColorPalette");
const svgToDataUri = require("mini-svg-data-uri");

export default {
  content: ["./src/**/*.{js,ts,jsx,tsx}"],
  theme: {
  },
  plugins: [
    function ({ matchUtilities, theme }: { matchUtilities: any; theme: any }) {
      matchUtilities(
        {
          "bg-grid": (value: string) => ({
            backgroundImage: `url("${svgToDataUri(
              `<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32" width="32" height="32" fill="none" stroke="${value}"><path d="M0 .5H31.5V32"/></svg>`
            )}")`,
          }),
        },
        { values: flattenColorPalette(theme("backgroundColor")), type: "color" }
      );
    },
  ],
} satisfies Config;
```

- 참고
  - [Jordi ⌘ on Twitter: "Mix it with a gradient-bg to make your cards more interesting 👨‍🎨 https://t.co/DANquDhesX" / Twitter](https://twitter.com/jordienr/status/1680147253535670273)
  - [Tailwind SVG Grid Background](https://gist.github.com/jordienr/abb847bc1649b3259d5aec1381583fd1)
