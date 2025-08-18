
```
npx create-next-app

√ What is your project named? ... portfolio
√ Would you like to use TypeScript? ... No / Yes
√ Would you like to use ESLint? ... No / Yes
√ Would you like to use Tailwind CSS? ... No / Yes
√ Would you like your code inside a `src/` directory? ... No / Yes      
√ Would you like to use App Router? (recommended) ... No / Yes
√ Would you like to use Turbopack for `next dev`? ... No / Yes
√ Would you like to customize the import alias (`@/*` by default)? ... No / Yes
```

- dependencies are managed by this command

Extra Options:
- Prettier
`npm install -D prettier eslint-config-prettier eslint-plugin-prettier

create .prettierrc :
```
// .prettierrc
{
  "singleQuote": true,
  "semi": true,
  "tabWidth": 2,
  "printWidth": 100,
  "trailingComma": "all",
  "jsxSingleQuote": true
}
```

eslint.config.mjs :
```
import prettierConfig from "eslint-config-prettier/recommended";
...
const eslintConfig = [
  ...
  prettierConfig, // add at end
];
```

package.json :
```
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint",
    "format": "prettier --write \"**/*.{js,jsx,ts,tsx,json,css,md}\"",
    "lint:fix": "npm run lint -- --fix"
  },
```

init tailwind config file:
`npx tailwindcss init -p` (NO LONGER NECESSARY FOR CSSv4)
INSTEAD, just check the css file
