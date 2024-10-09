- ## [Using React](https://tailwindcss.com/docs/guides/vite#react)
    

1. ## Create your project
    
    Start by creating a new Vite project if you don’t have one set up already. The most common approach is to use [Create Vite](https://vitejs.dev/guide/#scaffolding-your-first-vite-project).
    
    Terminal
    
    ```
    npm create vite@latest
    ```
    
2. ## Install Tailwind CSS
    
    Install `tailwindcss` and its peer dependencies, then generate your `tailwind.config.js` and `postcss.config.js` files.
    
    Terminal
    
    ```
    npm install -D tailwindcss postcss autoprefixernpx 
    
    ```

      ```
    tailwindcss init -p 
    
    ```

1. ## Configure your template paths
    
    Add the paths to all of your template files in your `tailwind.config.js` file.
    
    tailwind.config.js
    
   
      content: 
        "./index.html",
        "./src//.{js,ts,jsx,tsx}",
    
    ```
    
4. ## Add the Tailwind directives to your CSS
    
    Add the `@tailwind` directives for each of Tailwind’s layers to your `./src/index.css` file.
    
    index.css
    
    ```
    @tailwind base;
    @tailwind components;
    @tailwind utilities;
    ```
    
5. ## Start your build process
    
    Run your build process with `npm run dev`.
    
    Terminal
    
    ```
    npm run dev
    ```
    
6. ## Start using Tailwind in your project
    
    Start using Tailwind’s utility classes to style your content.
    
    App.jsx
    
    ```
    export default function App() {
      return (
        <h1 className="text-3xl font-bold underline">
          Hello world!
        </h1>
      )
    }
    ```