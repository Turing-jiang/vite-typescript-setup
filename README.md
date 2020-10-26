# vite-typescript-setup
### Use typescript in vue3 with vite  
* First, create a vite project  
  ```shell
  $ npm init vite-app <project-name>
  $ cd <project-name>
  $ npm install
  ```
* Second, install typescript
  ```shell
  $ npm install typescript
  ```
* Third, create a tsconfig.json file in the root folder, like this:  
  ```json
  {
  "compilerOptions": {
    "target": "esnext",
    "module": "esnext",
    "moduleResolution": "node",
    "importHelpers": true,
    "isolatedModules": true,
    "noEmit": true
    }
  }
  ```
  And you can check here, What is a [tsconfig.json](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)  
* Then, create a shims-vue.d.tsfile in the src folder, like this:  
  ```typescript
  declare module "*.vue" {
    import { defineComponent } from "vue";
    const Component: ReturnType<typeof defineComponent>;
    export default Component;
  }
  ```
  The `shims-vue.d.ts` file helps your IDE to understand what a file ending in `.vue` is.  
  Now, we can check whether the `.ts` file works well.  
  In my case, I rename the `main.js` file to `main.ts` in the src folder,  
  and modify the `index.html`, 12 line:
   ```html
   <script type="module" src="/src/main.js"></script> 
   ```
   to
   ```html
   <script type="module" src="/src/main.ts"></script> 
   ```
   At last, run
   ```shell
   $ npm run dev
   ```
  If there is no error message, you can create your component file by `.ts`.
  Change the `<script>` to `<script lang='ts'>`, and define components with [defineComponent](https://v3.vuejs.org/guide/typescript-support.html#defining-vue-components) global method.

