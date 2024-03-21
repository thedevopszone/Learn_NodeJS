# Learn NodeJS


```
mkdir Kindle
cd Kindle

npx create-next-app@latest next-hello-world
cd next-hello-world

# For Prod
npm run build

# For Dev
npm run dev

npm run start

```


## Install Tailwind

```
npm install -D tailwindcss postcss autoprefixer
```

Create tailwind config files (postcss.config.js and tailwind.config.js)
```
npx tailwindcss init -p
```




vi tailwind.config.js
```
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./pages/**/*.{js,ts,jsx,tsx}",
    "./components/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}

```

vi styles/globals.css
```
@tailwind base;
@tailwind components;
@tailwind utilities;
```

vi app/page.tsx
```
export default function Home() {
  return (
    <div className="flex h-screen w-screen items-center justify-center">
      <p className="text-bold">Hello World!</p>
    </div>
  );
}

```


Start App
```
npm run dev
```


Code at: https://github.com/higracehuang/next-hello-world
```
git clone https://github.com/higracehuang/next-hello-world
cd next-hello-world

npm install

npm run build

npm run dev
# or
npm run start
```






