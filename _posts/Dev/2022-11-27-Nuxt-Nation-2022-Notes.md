---
title: Nuxt Nation 2022 Notes
layout: post
author: Mostafa Lotfy
section: Dev
permalink: /dev/nuxt-nation-2022-notes
image: /assets/i/nuxt-nation-2022/nuxt-nation-2022-thumbnail.png
---

## On This Page
1. [Nuxt Nation](#nuxt-nation)
2. [Nuxt 3.0 Stable](#nuxt-3-stable)
3. [Client-side Error Handling In Nuxt](#client-side-error-nuxt)
4. [Vue Js Composables](#vue-composable)
5. [Nuxt Image](#nuxt-image)
6. [Vue Macros](#vue-macros)
7. [Nuxt Rendering Modes](#nuxt-rendering-modes)
8. [Nuxt Custom Dev Tools](#nuxt-custom-dev-tools)
9. [How Nuxt 3 is allowing us to build faster apps](#nuxt-3-faster-apps)
10. [Comparing Nuxt 2 to Nuxt 3](#nuxt3-vs-nuxt2)
11. [Multi-Variant Apps With Nuxt3](#multi-variant-apps)
13. [Building and deploying mobile apps with Nuxt/Ionic](#nuxt-ionic)
14. [Good solutions for working with Icons in Nuxt](#nuxt-icons)
15. [Why use Nuxt when you can do it yourself with Vite? (Nuxt Vs. Vite functionalities differences](#nuxt-vs-vite)
16. [How do you balance your primary job with maintaining open-source projects?](#work-balance)
17. [Does `npx nuxi generate` scale? Is there a plan for an ISR (incremental static regeneration)?](#isr-nuxt)
18. [Are there any other big meta frameworks like Nuxt that use Vite?](#meta-frameworks-with-vite)
19. [Which is better to create a large app Next.js or Nuxt.js?](#nuxt-vs-next)
20. [Micro-frontend Architecture in Nuxt 3?](#Micro-frontend-in-nuxt)
21. [Can you talk about clean architecture and why we should or should not apply it to frontend development?](#clean-architecture-frontend)
22. [How to use concurrency and interval properties in NuxtJs static mode, when there are many headless cams data API calls on hundreds of pages?](#concurrency-in-nuxt-static)
23. [What is the process of becoming a Nuxt ambassador?](#become-nuxt-ambassador)
24. [What are the next big steps for Nuxt, Vite, and Vue?](#vue-next-steps)
25. [Nuxt In Large Companies](#nuxt-in-large-companies)
26. [Nuxt Extends](#nuxt-extends)
27. [Pinceau](#pinceau)
28. [End-to-End Type Safety with Nuxt and tRPC](#nuxt-trpc)
29. [Add 3D to your Nuxt app with Three.js](#nuxt-threejs)
30. [UNJS and Nuxt 3](#unjs-nuxt3)
31. [What is headless?](#what-is-headless)
32. [Nuxt Security](#nuxt-security)
33. [Supercharged `<head>` management](#head-management-nuxt)
34. [Beyond Static: Building with Nuxt 3 and Nitro](#nuxt-3-nitro)
35. [Tools To Explore](#tools)

## [Nuxt Nation](https://nuxtnation.com/) {#nuxt-nation} 

Nuxt Nation is an online event that is held by Vue School, with speakers such as the Nuxt and Vue authors.

These are some notes I took while attending the online conference on 16 & 17 November 2022.

Some of the talks, that I took notes from can be found on the [Vue School YT channel](https://www.youtube.com/@vueschool3782/videos){:target="_blank rel="noreferrer"}

There are [Free workshops](https://nuxtnation.com/workshops){:target="_blank rel="noreferrer"} from Nuxt Nation, with limited seats.

## Nuxt 3.0 Stable {#nuxt-3-stable}

![Nuxt 2 vs Nuxt 3](/assets/i/nuxt-nation-2022/Nuxt3-vs-nuxt2.png)

- Vue2 used connect which is used by ExpressJs, now they use h3 which is one of the fastest Js frameworks and works in any environment (node, Cloudflare workers, ...)
- Vue Router 4 is not included by default if you do not have a `pages` directory.
- Nitro is a server, it uses h3 under the hood, but it's also a bundler (it will track all the dependencies and delivers an output that is less than 1 mega bite and can be deployed on any platform including Cloudflare workers)

![Nuxt 3 javaScript size vs Nuxt 2](/assets/i/nuxt-nation-2022/nuxt3-js-size-vs-nuxt2-js-size.png)

- Out of the 34.1KB, Vue is 25.3 and Nuxt is 8.7kB

![Nuxt 3 is fast, it has Hybrid rendering, and SEO and web vitals](/assets/i/nuxt-nation-2022/nuxt-3-features.png)

- Auto imports.
- Components inside the `component` directory can be used without import.
- Pages directory. Each file is mapped to a route.

- `server/` directory allows you to go full stack with Nuxt with a database. 
- `composables/` Nuxt is shipped with many composables to help manage App data, and you can add your own.
- Modules.
- content directory for building pages with markdown.

## Client Side Error Handing In Nuxt {#client-side-error-nuxt}

- [Michael Thiessen](https://michaelnthiessen.com/){:target="_blank rel="noreferrer"}

- End users are unpredictable.
- Something unexpected will happen.
- Instead of the app crashing we need to handle these errors.
- `createError` method is provided by `Nuxt` and it works on the client side and server side.

```vue
<template>
	<lessonCompleteButton
		:model-value="isLessonComplete"
		@update:model-value="
			throw createError('could not update');	
		"
	/>
</template>
```

- To handle the above error in a nice way using the `<NuxtErrorBoundry />` component. It allows us to isolate errors, instead of relying on the generic error. The whole app doesn't crash just this specific part.
- Any error that happens within the boundaries of this container will be handled
- There will be no error in the console as the `NuxtErrorBoundry` will catch it.
- It switches between rendering the default slot and the error slot. Which allows us to put an error message.
- If the part with the error crashes we can then still use the rest of the app.

```vue
<template>
	<NuxtErrorBoundry @error="LogSomeError">
		<!-- wrap it around the parent component that holds the component with the createError method -->
		<NuxtPage />
		<template #error="{ error }">
			<p>
				Oh no, something broke!
				<code>{{ error }}</code>
			</p>
		</template>
	</NuxtErrorBoundry>
</template>
```

- It's not enough to catch the error, we want to reset it (set its value to null)

```vue
<template>
	<NuxtErrorBoundry @error="LogSomeError">
		<!-- wrap it around the parent component that holds the component with the createError method -->
		<NuxtPage />
		<template #error="{ error }">
			<p>
				Oh no, something broke!
				<code>{{ error }}</code>
			</p>
			<p>
				<button
					@click="resetError(error)"
				>
					Reset
				</button>
			</p>
		</template>
	</NuxtErrorBoundry>
</template>

<script setup>
const resetError = (error) => {
	error.value = null
}
</script>
```

- Also before resetting it we must try to resolve the error to not get stuck in a loop of resetting and then getting the same error again.
- How to resolve depends on the context and the expected errors. One way to do so is to navigate to a safe place away from the error. And we can do this using the `navigateTo` method.

```vue
<template>
	<NuxtErrorBoundry @error="LogSomeError">
		<!-- wrap it around the parent component that holds the component with the createError method -->
		<NuxtPage />
		<template #error="{ error }">
			<p>
				Oh no, something broke!
				<code>{{ error }}</code>
			</p>
			<p>
				<button
					@click="resetError(error)"
				>
					Reset
				</button>
			</p>
		</template>
	</NuxtErrorBoundry>
</template>

<script setup>
const resetError = async (error) => {
	await navigateTo(
		'/course/chapter/1-chapter-1/lesson/...'	
	)
	error.value = null
}
</script>
```

Common errors
- Networking requests
- User Inputs
- Redirects

createError method has the option to create a fatal error. If it's an error we can't recover from you can use it to though a full-screen error.

error monitoring systems

`NuxtErrorBoundry` Vs v-if
- Not much

If you navigate away without resetting the error the error will still be there. Then it's best to do some sort of middleware that resets errors or perhaps a key on the `NuxtErrorBoundry` that is key to the route that you're on so each time you navigate away it forces it to reset the error.

The error can return an object as well as a message.

## Vue Js Composables {#vue-composable}

- Inside a composable directory you can refactor code that you repeatedly use.
- Nuxt will automatically pick up that you created the composable and you can use it in your pages script tag and it will be automatically imported.
- Then when you update your composable the changes will apply to all your pages.

```vue
<!-- /pages/about.vue -->

<template>
	<!-- ... -->
</template>

<script setup>
const title = 'About'
const description = '...'

useSimpleHead({ title, description }) // You can just add this line to all your pages.

</script>
```

```vue
<!-- /composables/useSimpleHead.ts -->

export default ({ title, description }) => {
	useHead({
		title,
		meta: [
			{ hid: "description", name: "description", content: description },
			// Open Graph
			{ hid: "og:title", name: "og:title", content: title },
			{ hid: "og:description", name: "og:description", content: description },
			// Twitter
			...
		]
	})
}
```

## Nuxt Image {#nuxt-image}

[https://v1.image.nuxtjs.org](https://v1.image.nuxtjs.org){:target="_blank rel="noreferrer"}

install 
`yarn add --dev @nuxt-image-edge`

A package that allows you to resize and transform your images using a built-in optimizer or your favorite image CDN

add the model in the `nuxt.config.ts` file

```ts
export default defineNuxtConfig({
	modules: [
		'@nuxtjs/tailwindcss',
		'@nuxt/image-edge',	
	]
})
```

Use `<nuxt-img>` tag instead of the `<img>` tag inside your components

```vue
<!-- app.vue -->

<template>
	<div class="...">
		<nuxt-img 
			src="/images/my-image.jpeg"
			width="750"
			height="350"
			format="avif"	
		>
		<nuxt-picture
	</div>
</template>
```

You can also use the `<nuxt-picture>` tag

```vue
<!-- app.vue -->

<template>
	<div class="...">
		<nuxt-image
			src="images/my-image.jpeg"
			
		>
	</div>
</template>
```

## Vue Macros {#vue-macros}

- A series of proposals of ideas that are not yet officially implemented by Vue.

![defineModel code example](/assets/i/nuxt-nation-2022/defineModel.png)

![defineModel with reactivity transform code example](/assets/i/nuxt-nation-2022/defineModel-with-reactivity-transform.png)

macro vs runtime code
a macro allows more complicated features to be implemented. 

## Nuxt Rendering Modes {#nuxt-rendering-modes}

[Nuxt rendering docs](https://nuxt.com/docs/guide/concepts/rendering/){:target="_blank rel="noreferrer"}

- In a traditional Vue App, each page is rendered on the client side. Which can improve the app's performance, but creates SEO issues.
- Nuxt allows universal rendering. The server provides the browser with a fully rendered page, then it acts as SPA. Fixing the SEO issues, yet still providing the performance of a SPA.
- Hybrid Rendering. No need to choose just one rendering mode for the whole app (client or server-side rendering). You can define rendering rules for a group of routes. 
- We can for example set a blog as a static that gets rendered only once, then set another part of the app to be SSR.

## Nuxt Custom Dev Tools {#nuxt-custom-dev-tools}

use-cases
- Activate/deactivate Feature flags
- Intercept and modify requests
	- Offline development mock responses
- Fake user roles
- Trigger app events
- Share configuration with other stakeholders


What are feature flags?

can be used for beta testing
```js
if (featureFlag['newFeature'] === true) {
	renderNewFeature()
	changeAppBehavior
}
}
```
can be used for a/b testing
```js
if (featureFlag['experiment-A'] === true) {
	buttonCssClass = 'text-green'
}
```
deploy without risks
```js
if (featureFlag['risky-feature'] === true) {
	compute()
}
```
Roll back without code changes
```js
if (featureFlag['it-wasnt-me'] === true) {
	throw new Error('opps!')
}
```
Test performance profiling
```js
if (featureFlag['test-pref'] === true) {
	await newQuery()
} else {
	await oldQuery()
}
```
Kill switches
```js
// For example disable some features on a given day
if (featureFlag['kill-feature'] === true) {
	compute()
}
```
- Maintenance mode
-  Sunsetting
```js
if (featureFlag['goodbye-feature'] === false) {
	continueWithFeature()
}
```

`npx nuxi init -t module my-module`


[@nuxt/kit](https://v3.nuxtjs.org/api/advanced/kit){:target="_blank rel="noreferrer"}
A library that encapsulates all the methods you'll need to create Nuxt modules.



```ts
export default defineNuxtModule<ModuleOptions>({
	meta: {
		name: "module-name",
		configKey: "module-key-in-nuxt-config"
	},
	defaults: {
		// default module config
	},
	setup(options, nuxt) {
		// add plugins, components, etc	
	}
})
```


## How Nuxt 3 is allowing us to build faster apps {#nuxt-3-faster-apps}

![As page load speed increases conversion rate decreases](/assets/i/nuxt-nation-2022/frontend-speed-conversion.png)

- Frontend is king.
- 70% of customers admit that page speed impacts their willingness to buy from an online retailer. Deloitte
- Frontend drives revenue.
- Building SPAs improves the UX but there's much more that goes into creating a good UX than just that. 
- JavaScript meta-frameworks (like Nuxt or Next) emerged to reduce the workload and make you focus on building the front end. They improve the developer experience.
- Performance is fundamental. Performance is key for the user experience. The design will not be noticed if the performance is bad.
- what is performance
	- The objective measurement of a perceived user experience of a website or application. MDN. 
	- Core web vitals are key.
	- The only metric that is going to tell you if the experience is good or bad is revenue. So good core web vitals do not necessarily mean that the experience is good, but bad core web vitals do mean that the experience is bad.

![Core web vitals: LCP (largest contentful paint), FID (first input delay), and CLS (cumulative layout shifts)](/assets/i/nuxt-nation-2022/LCP-FID-CLS.png)

What makes a good performance?
- Main content is visible in less than 2.5 seconds.
- First interaction is delayed less than 100ms.
- Less than 10% of elements change their position during page loading.

Metrics from builder.io

![Simple to do app speed comparison across different front end frameworks](/assets/i/nuxt-nation-2022/todo-app-frontend-frameworks-speed-comparison.png)

![Complex app speeds comparison across different frontend frameworks](/assets/i/nuxt-nation-2022/complex-app-frontend-frameworks-speed-comparison.png)

Benchmarks are useful but they are not the ultimate source of truths. So many things that can influence benchmarks.

CLS (Cumulative Layout Shifts)

Things that can cause layout shifts
- FOUC (Flash of un-styled content) 
- Happens when the HTML is rendered before the CSS
- Nuxt inlines the global CSS and the CSS from the current page inside the index HTML.
- Problem CSS is render-blocking, so the page won't render until the whole CSS is. Thus it's extremely essential to inline CSS that is crucial (that will cause FOUC) and nothing more.
- Nuxt solves this by inlining the critical CSS only. The CSS is above the fold.
- To inline only critical (above the fold) CSS you can use @nuxtjs/critters plugin. Requires zero configuration. Critters a library from google.

- FOUT (flash of unstyled text) or FOIT (Flash of invisible text)
Especially when using a 3rd party font.
a common way is to display fallback font
Use the nuxt-font-metrics module to it automatically


To improve LCP and FID
- Reduce the amount of JS
- Follow the Purple pattern
	- Preload most important assets
	- Render the initial route ASAP
	- Prefetch remaining assets
	- Lazy-load other routes and secondary assets
- Nuxt Js automatically does code splitting. Splitting each route into a separate bundle.
- Also nuxt auto imports the components and composables for each page to make sure nothing is redundant

- 32kB initial bundle size
- 0 ms total blocking time as a foundation
- automatic imports and code splitting to keep the bundle small
- Prefetching other routes, when they click on it they don't have to download, just the Js will be executed. (Downloading the code that we need in the future in advance)
- Nuxt is not blindly prefetching all the possible routes. 
	- By using `<NuxtLink>` as soon as those links appear in the viewport.

```vue
<NuxtLink to="path" prefetch>
	This link will be prefetched, when it appears in the viewport
</NuxtLink>
```

- Lazy-loading secondary content is the developer's job. 

### Nuxt on the Edge
- For some content just has to be dynamically rendered, and it's best to do this on the edge (the location that is closer to the user)
- This requires running Nuxt on the edge function
- Every time you run a cloud function, every time you call it it has to cold start the whole app. This used to take 314ms in Nuxt 2, now using nitro it takes 3ms only.
- Cloud function have a limitation on disk space and went down from 51 152 KB in Nuxt 2 to 716 kB using nitro.

![Different hosting providers (including cloudflare, netlify, and Vercel) that Nitro works with](/assets/i/nuxt-nation-2022/nitro-engine-toolbox.png)

## Comparing Nuxt 2 to Nuxt 3 {#nuxt3-vs-nuxt2}

- Now working with Vue3 instead of Vue2

![Vue 3 main features; increased performance, TypeSCript support, and it works with composition API](/assets/i/nuxt-nation-2022/nuxt-best-features.png)

- Adding more features to Universal Rendering

![Nuxt 3 has better performance, improved SEO, and allows for fast static site generation](/assets/i/nuxt-nation-2022/nuxt3-universal-rendering-improvements.png)

![Nuxt 3 runs anywhere, built for fast cold starts, and supports hybrid rendering](/assets/i/nuxt-nation-2022/Nuxt-3-universal-rendering.png)

[Hybrid Rendering in Nuxt.js 3](https://vueschool.io/articles/vuejs-tutorials/hybrid-rendering-in-nuxt-js-3/){:target="_blank rel="noreferrer"}

![Zero-config Nuxt deploys on different platforms including Cloudflare pages, Vercel, and Netlify](/assets/i/nuxt-nation-2022/Nuxt-3-zero-config.png)

![Nuxt 2 used Webpack and CLI tooling](/assets/i/nuxt-nation-2022/nuxt-tooling.png)

![Nuxt 3 supports Vite and Nuxi CLI tooling](/assets/i/nuxt-nation-2022/nuxt3-tooling.png)

File structure
- `/pages`
	- Dynamic Params syntax changed
		- `/pages/[id].vue`
		- `/pages/edit-[id].vue`
	- To define page meta
```js
definePageMeta({
	middleware: ["auth"],
	pageTransition: 'fade',
	layout: 'blog',
})	
useHead({
	title: "Hello World"
})
```
- `/components`
	- Components (and composables) are both auto imported
	- To render a component on the client side only you can wrap it in `<clientOnly>` element like in Vue 2, but you can now name the component's file itself like this: `MyComponent.client.vue` instead.
	- lazy load components by prefixing with "lazy" `<LazyMountainList v-if="show" />`
	- You can combine a directory structure to assemble a component name
	
![Nuxt 3 components directory](/assets/i/nuxt-nation-2022/nuxt-components-directory.png)

- `/layouts` directory
	- extract common UI or code patterns into reusable layouts

![Nuxt 3 render page must be wrapped and uses slot element](/assets/i/nuxt-nation-2022/nuxt-slot.png)
- `/middleware`
	- run code before navigating to a route
	- define a global middleware by appending `.global` to the end of the file name. `~/middleware/log.global.js`
	- Middleware definition
	```js
	// middleware/log.js
export default defineNuxtRouteMiddleware((to, from) => {
	return navigateTo('/login') // a redirect
})	
```
- `/plugins` 
	- Provide global helpers, registers Vue plugins, and directives
	- In Nuxt 3 they are auto-registered based on their presence in the **/plugins** directory. No need to manually register them in **/nuxt.config.ts**
	![[Pasted image 20221118160839.png]]
- Just use composable instead of helper functions.
- `/static` directory has become the `/public`
- `/store` store or state management directory from Vue 2 no longer exists
- A `const useX = () => useState('x')` is available out of the box, or you can choose to install Pinia for global state management.
- `server` directory has been added to Nuxt 3
![[Pasted image 20221118161518.png]]
- Nuxt Bridge
	- Will bring Nitro, Vite, Composition API, Script setup, Auto imports, and other features will be backported to your Nuxt 2 project. Then you can start to incrementally migrate.
	- There are some steps it's not installed and it's done.

## Multi-Variant Apps With Nuxt3 {#multi-variant-apps}

- Use theming and configs as the base of multiple Nuxt projects.
- Projects that have a designated version per customer.
- Use domain-driven design in a Nuxt project
![[Pasted image 20221118192202.png]]

- Possible via Nuxt's hooks and module system.
- But, you'll be fighting against Nuxt's default folder structure. Has to be done for every project.
- `extends`
	- Extend your Nuxt app based on other (partial) apps
	- Can be used from a local folder, npm packages, and git repos* (no dependencies are going to be installed when you pull it from a git repo)
	- Uses unjs/c12 under the hood.
	
```js
// A simple example
// single base app, e.g. a theme
export default defineNuxtConfig({
	extends: 'content-wind' // a tailwind starter template
})
```

```js
// Use multiple sources
export default defineNuxtConfig({
	extends: [
		'../base-app',
		'github:manniL/nuxt-extends-test',
		'../feature-ecommerce-shopify',
		'../feature-tracking-plausible'	
	]
})
```

- Each of the sources will be transformed into a layer
- Supports all the benefits of the special Nuxt folders
- Full IntelliSense, HMR, and TS support
- Auto imports
- Layers can override previous layers

`app.config.{ts,js}`
	- Exposes reactive config for your app
	- Can be updated during runtime
	- Will be added to the client only - don't add secrets!
	- Full HMR support
	- `useAppConfig` composable to retrieve app config
	- Infers types based on the provided config
```
export default defineAppConfig({
	socials: {
		twitter: 'TheAlexLichter'	
	}
})
```
```vue
<script setup lang='ts'>
	const appConfig = useAppConfig()
	console.log(appConfig.socials.twitter) // 'TheAlexLichter'
</script>
```
- Can be used for anything
	- design tokens
	- social links
	- branding text
	- Throughout the layers (sub-applications) you can reference that.

Caveats
- Aliases are always resolved to the final app
	- Don't use `@`, `~`, ... instead, use relative paths (but only in the sub apps)
- Unexplored - only a few usage examples out there, e.g.:
	- [Docus](https://github.com/nuxt-thems/docus){:target="_blank rel="noreferrer"}
	- [Typography](https://github.com/nuxt-themes/typography){:target="_blank rel="noreferrer"}
	- [Content wind](https://github.com/Antiux/content-wind){:target="_blank rel="noreferrer"}
	- [config-extends](https://github.com/nuxt/framework/tree/main/examples/advanced/config-extends){:target="_blank rel="noreferrer"}
- Hooks from `nuxt.config.{ts,js}` are not yet merged - use modules instead.
- Not in the Docs yet.


Upcoming features
- Named layers - access files from layers via named alias
	- e.g. `~layerName` - `~layerName/assets/logo.png`
- Follow #3222 for updates of `extends`

## Building and deploying mobile apps with Nuxt/Ionic {#nuxt-ionic}

- [Presentation Link](http://ionic.link/3f385om){:target="_blank rel="noreferrer"}
- [Demo repo](https://github.com/ceceliacreates/nuxt-ionic-demo/blob/main/pages/index.vue){:target="_blank rel="noreferrer"}

### Why Nuxt/Ionic?
- Nuxt benefits brought to mobile.
- A Nuxt module that you can add to your existing project with zero config
- Leverage the power of Ionic and Capacitor
- Native look-and-feel

### What is Ionic

### What is Capacitor


### Nuxt Ionic Features
- Auto import all Ionic components, icons, and composables.

- Out of the box Page Routing.
- Leverages IonRouter, and handles nice animations as you navigate.
- Access the router via `useIonRouter()`
- Support for Nuxt routing utils like `definePageMeta()`

- Theming
- Override styling via exposed CSS props

- Built-in utility functions
- via the auto-imported compassables
- Swiping gestures
- Animations
- ...

### Capacitor
- Open source native bridge; allows you to run a web app on a mobile device
- Easy access to common device features; camera, geolocation, file picker, ... (things you need to interact with the device you're building for)
- Run on IOS and Android devices

### Getting Started with Nuxt/Ionic

0. Create a starter Nuxt 3 app

`npx nuxi dev`

1. Add Nuxt/Ionic Module

`npm install @nuxtjs/ionic -D`

```ts
// /nuxt.config.ts

export default defineNuxtConfig({
	target: "static",
	modules: ['@nuxtjs/ionic']
})
```

```vue
// /app.vue

<!--ion-router-outlet allows you to use file-based routing, but gives you the look and feel as you navigate your mobile app-->

<template>
	<ion-app>
		<ion-router-outlet />
	</ion-app>
</template>
```

2. Set up routing

- Create a `/pages` directory.
- Create an `/pages/index.vue` page.
- Create a `/pages/resources.vue` page.

3. Use components & Icons

[Check the demo's GitHub repo](https://github.com/ceceliacreates/nuxt-ionic-demo/blob/main/pages/index.vue){:target="_blank rel="noreferrer"}

```vue
<!-- index.vue -->

<template>
	<!-- ion-page is the root component of any page in an ionic app -->
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Nuxt Ionic</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Nuxt Ionic</ion-title>
        </ion-toolbar>
      </ion-header>
      <div id="container">
        <h1>Hello Nuxt Nation 👋!</h1>

        <ion-button router-link="/resources">Get Started</ion-button>
      </div>
    </ion-content>
  </ion-page>
</template>

<style scoped>
#container {
  text-align: center;

  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}
#container strong {
  font-size: 20px;
  line-height: 26px;
}
#container p {
  font-size: 16px;
  line-height: 22px;

  color: #8c8c8c;

  margin: 0;
}
#container a {
  text-decoration: none;
}
</style>

<!-- No script tag as we don't need to import anything unlike using ionic/vue -->
```

```vue
<!-- /pages/resouces.vue -->

<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Resources</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Resources</ion-title>
        </ion-toolbar>
      </ion-header>
      <div id="container">
        <ion-list :inset="true">
          <ion-item>
            <ion-icon :icon="ioniconsBookOutline" slot="start"></ion-icon>
            <ion-label
              ><a
                target="_blank"
                rel="noopener noreferrer"
                href="https://ionic.nuxtjs.org/"
              >
                Nuxt Ionic Documentation</a
              ></ion-label
            >
          </ion-item>
          <ion-item>
<!-- ionic icons are auto imported :icon="ionicons*", start by ionicons then add the icon's name -->
            <ion-icon :icon="ioniconsRocketOutline" slot="start"></ion-icon>
            <ion-label>
              <a
                target="_blank"
                rel="noopener noreferrer"
                href="https://stackblitz.com/github/nuxt-modules/ionic/tree/main/playground"
                >Nuxt Ionic Playground</a
              ></ion-label
            >
          </ion-item>
          <ion-item>
            <ion-icon :icon="ioniconsLogoGithub" slot="start"></ion-icon>
            <ion-label>
              <a
                target="_blank"
                rel="noopener noreferrer"
                href="https://github.com/nuxt-modules/ionic"
                >Nuxt Ionic GitHub Repo</a
              ></ion-label
            >
          </ion-item>
          <ion-item>
            <ion-icon :icon="ioniconsVideocamOutline" slot="start"></ion-icon>
            <ion-label class="ion-text-wrap">
              <a
                target="_blank"
                rel="noopener noreferrer"
                href="https://www.youtube.com/watch?v=f4sB7NhCgRw"
                >Video: Getting Started with Nuxt Ionic Module for Nuxt 3 by
                Aaron Saunders</a
              ></ion-label
            >
          </ion-item>
        </ion-list>
        <ion-button router-link="/">Back</ion-button>
      </div>
    </ion-content>
  </ion-page>
</template>

<style scoped>
#container {
  text-align: center;

  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}
#container strong {
  font-size: 20px;
  line-height: 26px;
}
#container p {
  font-size: 16px;
  line-height: 22px;

  color: #8c8c8c;

  margin: 0;
}
#container a {
  text-decoration: none;
}
</style>
```

4. Update the theme

- Create a `/theme` directory.
- Create a `/theme/varibles.css` file

paste the CSS variables code

```css
/* ... */
```

- Update `nuxt.config.ts`
```ts
export default defineNuxtConfig({
	target: "static",
	modules: ['@nuxtjs/ionic'],
	css: ["@/theme/variables.css"]
});
```

- load the app `npx nuxi dev`
- Then enable dark mode from the chrome dev tools in the browser.
- It should change to dark mode

### Adding Capacitor to your Nuxt/Ionic project
1. Install Ionic CLI

- Gives us access to some capacitor commands.

`npm install -g @ionic/cli`

- Enable capacitor integration

`ionic integrations enable capacitor`

2. Add an android or IOS project
`ionic capacitor add android`

3. Build web code
we need to sync the android project with a web build version of our app.
- Create a build `npx nuxi generate`
-

4. Sync project
with capacitor.

`npx cap sync` -- This will copy the build to our android project

5. Open and run on mobile
- Start the app on a simulated android device
- Android studio and SDK should already be installed on your machine.
- You also need to have a device created to be able to pull up an emulator

`npx cap run android`
pick an emulator
It should open up and run

6. For IOS
The process is similar for IOS. 
You need XCode and Xcode CLI installed
Then replace any command that had android in it with IOS

### Deploying on Appflow

A cloud app management system built by ionic
a paid service

main features
- generates native binaries in the cloud
- Real-time code deployments/updates to users (live updates) (push changes to users using the web interface without needing the app store approval process)
- Automates app delivery to app stores

- connect your web repo using your version control of choice
- Create the web build that you built locally
- App flow will create a native build
- Allows you to deploy to app stores
- Allows you to push live updates

### Ionic Resources
- [Nuxt/Ionic Docs](https://www.google.com/url?q=https://ionic.nuxtjs.org/&sa=D&source=editors&ust=1669058207636519&usg=AOvVaw1G_pQoGJq3oazJEuOHsXwq){:target="_blank rel="noreferrer"}
- [Nuxt/Ionic playground](https://www.google.com/url?q=https://stackblitz.com/github/nuxt-modules/ionic/tree/main/playground&sa=D&source=editors&ust=1669058207636944&usg=AOvVaw1ezUaZYL35YRvYBwMBG-81){:target="_blank rel="noreferrer"}
- [Nuxt/Ionic GitHub](https://www.google.com/url?q=https://github.com/nuxt-modules/ionic&sa=D&source=editors&ust=1669058207637173&usg=AOvVaw19YFKEZ0mpCBjyqxnV2NPT){:target="_blank rel="noreferrer"}
- [Ionic Docs](https://www.google.com/url?q=https://ionic.io/docs&sa=D&source=editors&ust=1669058207637335&usg=AOvVaw1hSpn_yqDy8I0NLqeU776Y){:target="_blank rel="noreferrer"}
- [Capacitor Docs](https://www.google.com/url?q=https://capacitorjs.com/docs&sa=D&source=editors&ust=1669058207637491&usg=AOvVaw1_DZYalBcYIlb581V8opsS){:target="_blank rel="noreferrer"}
- [Appflow Docs](https://www.google.com/url?q=https://ionic.io/docs/appflow&sa=D&source=editors&ust=1669058207637621&usg=AOvVaw3FKx0An7w6xblgmlHfiWky){:target="_blank rel="noreferrer"}
- [Nuxt/Ionic Simple Demo App GitHub Repo](https://www.google.com/url?q=https://github.com/ceceliacreates/nuxt-ionic-demo&sa=D&source=editors&ust=1669058207637749&usg=AOvVaw00tA1eJL7Mz0w__6if2lcz){:target="_blank rel="noreferrer"}
- [Ionic Discord](https://www.google.com/url?q=http://ionic.link/discord&sa=D&source=editors&ust=1669058207637878&usg=AOvVaw03kMRAQ4ZHuVzalXvoQEBW){:target="_blank rel="noreferrer"}

- You can turn any web project you have into a mobile app using Capacitor, Ionic components are just what give you the native look and feel.


## Good solutions for working with Icons in Nuxt {#nuxt-icons}

- Nuxt-icon, uses Iconify. Nuxt's author is working on making it the one recommended solution.

## Why use Nuxt when you can do it yourself with Vite? (Nuxt Vs. Vite functionalities differences) {#nuxt-vs-vite}

- Nuxt provides an echo system for ready-to-use solutions
- Nuxt is stable
- Nuxt team works hard to make everything work out of the box
- The Nuxt team always recommends one Nuxt module solution that keeps working and behind the scenes they work on improving it. 

- Vite and Nuxt serve different goals. 
- Nuxt is a complete framework; it gives you conventions and a lot of conveniences, ... If you follow the recommended paths in Nuxt you'll be very efficient and Nuxt will abstract away a lot of the underlying complexities for you.
- Vite covers a lot of the common features that are shared between frameworks. When you go into SSR with Vite, you have to set up your SSR architecture (how to handle data fetching, routing page transitions, ...) all of these Vite is un-opinionated, so you have to figure that out yourself. It is not an easy feat to put everything together yourself.
- Vite is a shared common tooling layer that meta frameworks are built on. 
- So the question is are you trying to build your meta-framework using Vite, or do you want to use a meta-framework that is already polished (Nuxt)

## How do you balance your primary job with maintaining open-source projects? {#work-balance}
- Managing multiple big projects is a challenge.
- Find the right people.
- Build a team.
- Delegate.
- Let them take on more responsibilities.

## Does `npx nuxi generate` scale? Is there a plan for an ISR (incremental static regeneration)? {#isr-nuxt}

- When you use `nuxi generate` in Nuxt 3 it generates a fully static output that, during the build time, pre-renders every possible route and their data in the payload and you can deploy it on any hosting service.
- For a normal website (with the build of pages) it is possible at build time, but when we have lots of articles the build time gets longer and longer. And like a shop, we don't need to rebuild every possible page at runtime.
- Nuxt 3 has a built-in server that is portable enough to be hosted anywhere. If there is any page that we are sure it's not going to be regularly changed we define them on the build time they are prerendered and the rest of the pages would be directed on the runtime on an ISR basis.
- Route rules allow for this kind of hybrid rendering for ISR
- Static files are generated but are also integrated with the platform. This (currently) works for Vercel and Netlify. They are also natively bundled. And ISR works out of the box.
- What we have to do is define which routes we want to be generated on demand.

- For Netlify you don't need to use `Nuxt generate` you can use `Nuxt build`. You can specify what routes you want to pre-render by default so they will be static. Then any new pages will hit the lambda and will be cached until the next deployment. 
- It currently works with Nuxt 3 on Netlify and they are working with Vercel to have it supported.
- You can also use a caching layer and normal NodeJs and it will work as well.


## Are there any other big meta frameworks like Nuxt that use Vite? {#meta-frameworks-with-vite}

- Quaiser already supports using Vite.
- Vite press, a static site generator.
- Isles, a Vite-based meta-framework that uses island architecture.

- Astro is a Vite-based meta-framework that's framework agnostic.

## Which is better to create a large app Next.js or Nuxt.js? {#nuxt-vs-next}

- They both work.
- Both are fast.
- It's hard to compare performances. Marketing benchmarks are not accurate.
- Pick the one that makes you more productive. 
- Just because a lot of people are using a tool doesn't mean it's best for you.
- Evaluate based on your needs and preferences.
- Both Vue and react are massively popular and both provide good community support, so go with the one that better fits your mental model.

## Micro-frontend Architecture in Nuxt 3? {#Micro-frontend-in-nuxt}

- They had some experiments to support web components to integrate different apps. Through experience, they found out it doesn't work because Nuxt itself is like a host it can be integrated with some sub-apps like components, so they created a system called extends which can combine different apps and use Nuxt like a host.
- So right now it's not in the plan to support Microfrontend, 
- but there are hopes, as they are working on a new feature called component islands. Component islands are standalone and they can integrate with the whole application. They can, at some point, extract it and support different frameworks, Those components could run on any framework and be hydrated by themselves.

## Can you talk about clean architecture and why we should or should not apply it to front-end development? {#clean-architecture-frontend}

- If you're working with a frontend codebase typically your framework dictates the way you organize code already so you'd best follow the conventions of the framework you've chosen, instead of imposing too much architectural complexity on yourself. 
- Typically (these design patterns of clean architecture) these conventions are designed for situations where you have a really big team, for example, 100 devs working in a huge organization. If you're not in such an environment you don't have that problem.
- Could be a premature organization for writing code.
- A lot of front-end projects have smaller teams, unlike large back-end projects. 
- Most front-end projects don't need to go there.

## How to use concurrency and interval properties in NuxtJs static mode, when there are many headless cams data API calls on hundreds of pages? {#concurrency-in-nuxt-static}

- No specific option for it, it's automated. This is handled by Nitro.
- Or since you have more than a hundred pages, it's probably better to use hybrid rendering and ISR to generate on demand. Instead of pre-rendering all of them.

## What is the process of becoming a Nuxt ambassador? {#become-nuxt-ambassador}

- Right now there is no defined process.
- Thinking of a new program that allows everyone to get involved.
- They have the "Nuxt Insiders" that meets weekly to discuss their work, but this is mostly for module authors and contributors.
- Anyone is an ambassador by advocation, the Nuxt team is thinking about how to get ambassadors rewarded. Info will be given on this next year.
- Everyone is encouraged to write articles, and explain any project that uses Vue, Vite, or Nuxt. Until you get noticed.

## What are the next big steps for Nuxt, Vite, and Vue? {#vue-next-steps}

- For Vite. working on Vite 4, perhaps in a month. The main theme of the upgrade is upgrading to roll-ups 3 and other things that are related to the react echo system.
- For Nuxt: Component islands, improvements for hybrid rendering (the ability to specify at the page level). Improving modules to work seamlessly in Nuxt; image, auth. And lots of docs.
- For Vue: SSR-related improvements (built-in ability to lazy or on-demand hydrate async components), Vue Promote (new compilation strategy for Vue components) similar to solid Js, should result in better performance and better memory footprint, won't affect the way you write code, but the code should be faster, lighter, and more performant. Most improvements should also automatically benefit Nuxt users.

## Nuxt In Large Companies {#nuxt-in-large-companies}

Nuxt as a backbone of a scalable platform

JUMBO Showcase

Well-known offline and online grocery chains in the Netherlands and Belgium.
They develop a lot of their software in-house.
Over 300 devs working
 First, they grabbed an off-the-shelf solution. 
They started to add a couple of Vue components.
They grew and had different teams to specifically handle different customer journeys. They switched from a monolith to a distributed application architecture

![Jumbo adding Vue to the stack](/assets/i/nuxt-nation-2022/jumbo-stack-vue.png)

As the system evolved the complexities increased.

They were using Vue and their apps were using Vue components. 

So they build a component library.

 ![Jumbo using Vue, CMS, and component library to handle apps](/assets/i/nuxt-nation-2022/jumbo-stack-vue-cms-components.png)

![Jumbo added nuxt to the stack](/assets/i/nuxt-nation-2022/jumbo-stack-nuxt-vue-cms-components.png) 
 
A lot of maintenance for all these micro apps, and for the component library

What they wanted instead
	- Modular landscape
	- Independent moving parts (easily add or remove apps)
	- Simplify dependencies (simplify maintenance)

They considered using Nuxt as a simple app that would connect all these modules. They discarded this idea because they didn't want people to be working on the same codebase, depending on other teams' features to be delivered to deliver theirs.

Instead, they built their system

1. Built a component library. 
- Already part of their design system (to facilitate work between designers and devs)
- All components go here

2. CMS
- A means of getting data into your system
- It has to be headless
- Wrote an adapter to allow any CMS to be compatible with the system
- Connected to all the components in the component library

3. Content Service
- Newly built system (NodeJs)
- Brains of the platform
- Connects other systems
	- validates data models
	- does routing
	
4. Content Renderer
- Gets content from content service
- Needs to work with VueJs component
- Support SSR
- Nuxt is an obvious candidate

![Component library pointing to CMS](/assets/i/nuxt-nation-2022/jumbo-workflow.png)

![Headless CMS connected to the adapter. An adapter is connected to the content service. And Content service connected to a database.](/assets/i/nuxt-nation-2022/jumbo-workflow-cms.png)

![customer with an arrow pointed to nuxt. Nuxt pointed to CMS. And CMS pointing to database](/assets/i/nuxt-nation-2022/jumbo-stack-nuxt.png)

Challenges
- Map 100s of components & props to one editor UI (To solve this they extract component properties from Vue and give them back to the CMS as config. They can tell the CMS editor that a component has certain props.)
- Only ship what you need to reduce load (Nuxt components module allows them to read into all of the components that are being used on that page. So they tree shake everything per page and provide a per-page bundle)

It works for them. But they do use caching.

Which CMS does JUMBO use?
- Adobe experience manager.
- An enterprise-level CMS.
- What you see is what you get editing.
- It can also render and cache pages well.

## Nuxt Extends {#nuxt-extends}

- Allow you to extend one Nuxt application with another one.
- Theming is a perfect example of Nuxt extends usage.

How it works in code. 

```JSON
// ./package.json

{
	"private": true,
	"scripts": {
		"build": "nuxt build",
		"dev": "nuxt dev",
		"generate": "nuxt generate",
		"preview": "nuxt preview"	
	},
	"devDependencies": {
		"@nuxtjs/tailwindcss": "^6.1.0",
		"nuxt": "3.0.0-rc.12"
	},
	"dependencies": {
		// This will be used to extend our app
		"nuxt-commerce-theme": "^0.0.1"	
	}
}
```

```ts
// ./nuxt.config.ts

export default defineNuxtConfig({
	modules: ['@nuxtjs/tailwindcss'],
	extends: './node_modules/nuxt-commerce-theme'
})
```

Inspecting the "nuxt-commerce-theme" in the node-modules. You'll see that this package comes with the `nuxt.config.ts` file and a vue components folder that you can use in your app.

![](assets/i/nuxt-nation-2022/nuxt-extends-code-example.png)

So now we can add these components to our Nuxt app.

```vue
<!-- ./app.vue -->
<!-- All these components we haven't developed in our app, but were extends from another app -->

<template>
	<div>
		<HeroBanner />
		<TheFooter />
	</div>
</template>
```

So Nuxt extends to allow you to build reusable Nuxt themes.

## Pinceau {#pinceau}

[piceau](https://github.com/Tahul/pinceau){:target="_blank rel="noreferrer"}

- A new package for the Vue community.
- Aims at simplifying your work with Vue components by giving you a set of tools that will help you write and maintain CSS across your app.

- Design tokens configurations.
- CSS functions.
- Computed styles.
- Variants.

- Pinceau config is compatible with the design tokens format.
- Pinceau config is compatible with design tools like Figma and Sketch

## End-to-End Type Safety with Nuxt and tRPC {#nuxt-trpc}

- [trpc-nuxt.vercel.app](https://trpc-nuxt.vercel.app/){:target="_blank rel="noreferrer"}
- [trpc-nuct github](https://github.com/wobsoriano/trpc-nuxt){:target="_blank rel="noreferrer"}
- [trpc docs](https://trpc.io/docs){:target="_blank rel="noreferrer"}

### What is type safety?

Is when the compiler validates types while compiling, throwing an error if you assign the wrong type to a variable.

It just reduces a handful of bugs that you might not see otherwise.

### What is end-to-end type safety?

End-to-end type safety is having a single source of truth for your types across all the layers of your app.

![](assets/i/nuxt-nation-2022/what-is-end-to-end-type-safety.png)

If the User object changes for one of your layers, for the database for example, then it is going to require a lot of maintainabilities and more work. Can create issues, headaches, and a lot of work.

### Type Script Remote Procedure Call (tRPC)

- tRPC is a method of exposing server functions to the client in a typesafe manner.
- tRPC is only a solution when you're using type script on the backend and the front end.
- One way of thinking of tRPC is an alternative to REST and GraphQL

### How to use tRPC in a Nuxt application

- Install dependencies
`npm install @trpc/client @trpc/server trpc-nuxt zod`
- Add `trpc-nuxt` to your `nuxt.config.ts`
```ts
// nuxt.config.ts
export default defineNuxtConfig({
	modules: ['trpc-nuxt/module'],
	typescript: {
		strict: true,	
	}
})
```

- `@trpc/client` to make typesafe API calls from your client.
- `@trpc/server` for tRPC endpoints and routers
- `trpc-nuxt` Nuxt module built & maintained by wobsoriano
- `zod` server-side input validation

```ts
// server/trpc/trpc.ts
import { initTRPC } from '@trpc/server'

// Create the t-object and extract the helpers you plan on using
// Options include
	// Router
	// Procedure
	// Middleware

const t = initTRPC.create()

// Base router and procedure helpers

// Router provides a space to collect related procedures with a shared namespace
export const router = t.router
// Procedure can be viewed as rest endpoints that first validate the input using Zod, Yup, or Superstruct
export const publicProcedure = t.procedure
```

```ts
// server/trpc/routers/helloRouter.ts

// Import the router and procedure created in server/trpc/trpc.ts
import { z } from 'zod'
import { publicProcedure, router } from '../trpc'

// Call your router function and define your first procedure. You can think of this as an HTTP endpoint `apic/trpc/hello`
export const appRouter = router({
  hello: publicProcedure
	// Validate the input using Zod. Here we are defining an input parameter named text that expects a string.
    .input(
      z.object({
        text: z.string(),
      }),
    )
// .query() is the same as an HTTP GET request. Here it is taking the input defined above and returning something based on that input.
    .query(({ input }) => {
      return {
        greeting: `hello ${input?.text ?? 'world'}`,
      }
    }),
})
```

Another example; an Auth Router with a login procedure.

```ts
// server/trpc/routers/authRouter.ts

// Import the router and procedure created in server/trpc/trpc.ts
import { z } from 'zod'
import { publicProcedure, router } from '../trpc'

export const appRouter = router({
  hello: publicProcedure
	// Validate the input using Zod. Here we are defining an input parameter named text that expects a string.
    .input(
      z.object({
        text: z.string(),
      }),
    )
// We're calling the `.mutation()` function which is the equivalent of an HTTP POST request.
	.mutation(({ input }) => {
		// Here some login stuff would happen
		return {
			user: {
				name: input.name,
				role: 'ADMIN',
			},
		}
	}),
})
```


This is the entry point for your API and exposes the tRPC router.
This is where you can expose your API to middleware to manage things like CORS.

```ts
// server/api/[trpc].ts
import { createNuxtApiHandler } from 'trpc-nuxt'
import { appRouter } from '@/server/trpc/routers'

// export API handler
export default createNuxtApiHandler({
  router: appRouter,
  createContext: () => ({}),
})
```

Merging the routers into a centralized `appRouter`

```ts
// server/trpc/routers.ts

import { router } from '../trpc'
import { authRouter } from './authRouter'
import { helloRouter } from './helloRouter'

const appRouter = router({
	auth: authRouter,
	hello: helloRouter,
})

// export type definition API
export type AppRouter = typeof appRouter
```

The AppRouter type signature is passed to trpc-nuxt's `createTRPCNuxtPorxyClient` function.

Using `provide` to inject `trpc` into the client.

```ts
// plugins/trpc.ts

import { httpBatchLink, createTRPCProxyClient } from '@trpc/client'
import type { AppRouter } from '@/server/trpc/routers'

export default defineNuxtPlugin(() => {
  const trpc = createTRPCProxyClient<AppRouter>()
  return {
    provide: {
      trpc,
    },
  }
})

```

Using it will give you autocompletion on the client side.
Clicking on the query in the index.vue file (fort end) takes you directly to your back end (helloRouter.ts)
Refactoring queries and procedures. Changing them on the client site will change them automatically on the backend.

```vue
<!--index.vue-->

<script setup lang="ts">
const { $trpc } = useNuxtApp()

// query and mutate use useAsycData under the hood
const { data, pending, error } = await $trpc.hello.hello.query({ greeting: 'Nuxt Nation!' })
</script>

<template>
	<div v-if="pending">...loading</div>
	<div v-else-if="error?.data?.code">Error: {{ error.data.code }}</div>
	<div class="container" v-else>
		<p class="text">{{ data?.greeting }}</p>
	</div>
</template>

```

Does tRPC provide runtime validation or is it all about types for use at development time?
- Because it's only importing and exporting types. None of the code will be a part of the client. So once this is shipped the front end or the client has absolutely no idea of the backend, and that's one of the big benefits it's a very lean solution to this problem.

Is trpc-nuxt ready for production?
Not yet.

## Add 3D to your Nuxt app with Three.js {#nuxt-threejs}

- ThreeJS is a library that leverages WebGL to render 3D scenes on the web. (Basically makes it easier to use 3D in the browser)

First, we need to draw something

```js
const sphere = new Three.mech(
	// Geometry
	new THREE.SphereGeometry(1, 32, 32),
	// Material
	new THREE.MeshBasicMaterial({
		color: 0*008080	
	})
)
```

Then we need a camera to see it

ThreeJs has 2 types of cameras. We'll use perspective because it's the most similar to the human eye.

```js
const aspectRatio = 
	  window.innerWidth /
	  window.innerHeight

const camera = 
	  new THREE.PerspectiveCamera(
		 45, // FOV
		 aspectRation, 
		 0.1, // Near plane
		 1000 // Far plane 
	  )

camera.position.set(4, 4, 4)
```

A scene to put it all together

```js
const scene = new THREE.Scene()

// Adding our camera to the scene
scene.add(camera)

// Adding the sphere
scene.add(sphere)
```

A renderer to show it

```js
const renderer = new THREE.WebGLRenderer({
	canvas
})

renderer.setSize(
	window.innerWidth,
	window.innerHeight,
);

renderer.setPixelRatio(Math.min(window.devicePixelRatio))

renderer.render( scene, camera )
```

```vue
<script setup>
// ThreeJs related code ...
</script>

<template>
	<canvas />
</template>
```

This won't work  cause we didn't pass the reference for these canvas elements

Use TemplateRefs + Lifecycle hooks

```vue
<script setup lang="ts">
const experience: Ref<HTMLCanvasElement | null> = ref(null)
let renderer: WebGLRenderer

onMounted(() => {
	renderer = new THREE.WebGLRenderer({
		canvas: experience.value	
	})

	...
})
</script>

<template>
	<canvas ref="experience" />
</template>
```

It renders but it looks like an image. No interaction.

![](assets/i/nuxt-nation-2022/threeJs-sphere.png)

This is because we only render it once.

The Loop

The `requestAnimationFrame` function allows us to create a loop that runs at the browser's refresh rate.

```js
const loop = () => {
	
	// Move object 
	sphere.position.x += 0.01

	renderer.render( scene, camera );
	requestAnimationFrame(loop)
}

loop()
```

We have a sphere that animates smoothly.

Be mindful of reactivity


![](assets/i/nuxt-nation-2022/reactivity-and-threejs.png)

Nuxt + ThreeJS

The 3D world is not optimal for SSR, it might work but performance will not be optimal.

Nuxt allows you to use the `ClientOnly` component to render a component only on the client side.

```Vue
<template>
	<ClientOnly>
		<TheExperience />
	</ClientOnly>
</template>
```

Or you can add the `.client` suffix to the component file

![](assets/i/nuxt-nation-2022/nuxt-render-component-on-client.png)

Next steps
- Add light and different materials (MeshStandardMaterial, MeshPhongMaterial)
- Use textures (TextureLoader) 
- Add OrbitControls
- Add a model via GLTFLoader
- Animations with GSAP

Resources
- [ThreeJs playlist](https://www.youtube.com/playlist?list=PLi-X1Ojrrmi8hTTHRs2LprNaaZBDY5Mhk){:target="_blank rel="noreferrer"}
- [ThreeJS Journey by Bruno Simon](https://threejs-journey.com/#){:target="_blank rel="noreferrer"}

Any performance gotcha's that are important to watch out for when using ThreeJs with Nuxt?
- Try to update all the instances without reactivity.
- You can use a shallow ref and wrap to manage it, especially if using composable.
- Extract the logic from the experience and put it composables (all the logic for the render)

## [UNJS](https://unjs.io){:target="_blank rel="noreferrer"} and Nuxt 3 {#unjs-nuxt3}

[Presentation link](https://docs.google.com/presentation/d/1li7HfYo1ZTEnFCdpZuSO1k2ba5V7piGKat9NV_ryLVY/edit#slide=id.p){:target="_blank rel="noreferrer"}

unified Javascript tools.

![](assets/i/nuxt-nation-2022/unJs-rules2.png)

![](assets/i/nuxt-nation-2022/unjs-rules3.png)

[unjs/unbuild](htttps://github.com/unjs/unbuild){:target="_blank rel="noreferrer"}

Made for building Nuxt 3 modules and packages

[unjs/changelogen](htttps://github.com/unjs/changelogen){:target="_blank rel="noreferrer"}

Beautiful change logs using conventional commits
Used for Nuxt 3 releases notes and change-logs

[unjs/unplugin](https://github.com/unjs/unplugin){:target="_blank rel="noreferrer"}
Unified plugin system for Vite, Rollup, Webpack, and more.

[unjs/unimport](https://github.com/unjs/unimport){:target="_blank rel="noreferrer"}
A system that makes imports automated. Smartly tree shaken. ...

[unjs/ofetch](https://github.com/unjs/ofetch){:target="_blank rel="noreferrer"}

Better fetchAPI natively works on node, browsers, and workers.
Provides universal `$fetch` for Nuxt 3.

[node-fetch-native](https://github.com/unjs/node-fetch-native){:target="_blank rel="noreferrer"}
If you have a custom server or nodejs project. Future proof. Supports native fetch implementations for the server.

[unjs/h3](https://github.com/unjs/h3){:target="_blank rel="noreferrer"}

Minimal h(ttp) framework build for high performance, composition, and portability
Makes it easier to scale up the project.
Fast.
You can use h3 for any custom solution you have.
Nitro is built on h3.

[unjs/unstorage](https://github.com/unjs/unstorage){:target="_blank rel="noreferrer"}
Universal storage layer.
Cross-platform, Multi Driver KV storage powering Nuxt 3 and Nitro cache.
Persistent storage is one of the essential parts of making a universal framework.
You can combine different stores into a simplified key and value storage layer.
Used by Nuxt for caching and deployment
Works out of the box for any deployment platform

### [unjs/listhen](https://github.com/unjs/listhen){:target="_blank rel="noreferrer"}
- Elegant HTTP listener.
- Powering Nuxi CLI
- Small package with one single purpose to listen

### [unjs/c12](https://github.com/unjs/c12){:target="_blank rel="noreferrer"}
- Smart configuration loader.
- Powering Nuxt 3 and Nitro with extends and theming support.

### [unjs/ipx](https://github.com/unjs/ipx){:target="_blank rel="noreferrer"}
- High-performance, secure, and easy-to-use image proxy based on Sharp and libvips.
- Powering Nuxt Image and Next.js images on Netlify.
- If you want to optimize your images you can use Nuxt image, or if you have any custom solutions, or if you want to host it on a private CDN you can directly use ipx.

### [unjs/untyped](https://github.com/unjs/untyped){:target="_blank rel="noreferrer"}
- Generate config, docs, and types from schema and more
- powering Nuxt 3 config and schema
- Depends on one single schema config which is typescript, comments to define documentations and defaults, and normalization. Untyped generates the code and documentation.

### [unjs/giget](htttps://github.com/unjs/giget){:target="_blank rel="noreferrer"}
- Download templates and git repos
- Powering nuxi init

### [unjs/nitro](https://nitro.unjs.io){:target="_blank rel="noreferrer"}
- A powerful toolchain and runtime framework from the UnJs ecosystem to build and deploy any javascript server. anywhere.
- A meta-framework for Unjs.
- Combines different packages to make an experience similar to Nuxt but for the server side. ??


## What is headless? {#what-is-headless}

[Example app using Storyblok and Algolia with Nuxt](https://github.com/Baroshem/headless-avuengers){:target="_blank rel="noreferrer"}

- They don't come with their own UIs they are servers or software that we can communicate with by using an API.
- Examples
	- Storyblok
		- A headless content management system (CMS)
		- You add some content on Storyblok and fetch this data using an API in your NuxtJs website.
	- Algolia
		- A search and discovery platform
		- You can add results to the index and then search this index through your website
		- Also has a recommended API that learns from what customers are doing on your website. So it can (for an e-commerce website) recommend to the customer products based on their previous search.

Stack
- Nuxt Tailwind
- Nuxt Image
- Storyblok Nuxt
- Nuxt Algolia

## [Nuxt Security](https://nuxt-security.vercel.app){:target="_blank rel="noreferrer"} {#nuxt-security}

```shell
yarn add nuxt-security
```

Security module for Nuxt based on OWASP Top 10 and Helmet
Just by importing this module, you're making your app a bit more secure.

## Supercharged `<head>` management {#head-management-nuxt}

Vue head v1 and the future of SEO with Nuxt v3

HTML Metadata, Meta Info, Meta tags, Head tags

All the same.
Managing machine-readable elements and attributes outside the Vue render tree for SSR and DOM.

VueUse Head
`useHead` composable

```vue
<script setup>
useHead({
	title: 'My page title',
	meta: [
		{ name: 'description', content: 'My description'}	
	]
})
</script>
```

What does being a VueUse composable mean?

Accepts reactive arguments: ref, computed, and reactive getter.

```vue
<script setup>
const title = ref('My page title')
useHead({
	title
})
title.value = 'My new title'
</script>
```

Cleans up the side effect automatically, if it has any.

Avoid wrapping in watchers.

```js
// Bad
watch(ref, ()=>{
	useHead({title:ref.value})
})

// Good
useHead({title: ()=> ref.value})
```

What's going on with `useHead`
- Fully typed `useHead`
- Reactive getter support
![reactive getter code example](/assets/i/nuxt-nation-2022/nuxt-reactive-getter-support.png)
- Array support
- Prop promises
- DOM event handlers
![](assets/i/nuxt-nation-2022/nuxt-dom-event-handlers.png)

- unhead
	- New engine powering VueUse Head v1, now part of UnJS
	- Side-effect based: Less aggressive removal of tags and attributes. No more non-essential states in the DOM.
	- DOM rendering optimizations. 5x faster (-10ms CPU time for an average site)
	- Powered by hookable. Same hook system as Nuxt.
- Server-Only Tags
	- Rendering tags that would only render on the server. Such as inputs to assets URLs.

### Making SEO Easier

- useSEOMeta
	- Over 100+ definitions, powered by tree shaken.
	- intended to be tree shaken from the client build
	- Official Nuxt support coming soon (for now use it with manual imports, you can just import directly from the client)
	
![useSeoMeta code example](/assets/i/nuxt-nation-2022/useSeoMeta.png)

![Nuxt-unhead get early access to experimental features at github.com/harlan-zw/nuxt-unhead](/assets/i/nuxt-nation-2022/nuxt-unhead-experimantal.png)

### Practical Nuxt 3 SEO Tips

Performance
	- Nuxt server components (Stop hydrating things on the client side)
	- nuxt-fontaine
	- @nuxtjs/partytown
	- @nuxtjs/critters
	- issues (scan your site and give you a lighthouse report for it to fix accessibility and SEO issues)

SEO
	- nuxt-schema-org

### Do these meta tags have to be rendered server-side or will crawlers still find them when they're rendered on the client side?

Rendering on the server side is a safe option. 
Google said we're going to run your JS, so it might be fine.
However, server rendering them is highly recommended. No reason not to, unless you have a single-page app (SPA), in those instances Nuxt 3 will read your head config and throw that in the SPA's HTML template.

### Can useHead be used in custom composable?

useHead can be used anywhere, it's kind of like Pinia, it has a global state that we can reference rather than relying on the specific Vue setup state.
If you want to use useHead in middleware, custom composable go for it.
If you have any issues with it make an issue on the Nuxt repo or VueUseHead and they'll look into it.

### When would you choose to link CSS via useHead versus the CSS option in `nuxt.config`?
The Nuxt CSS option does some CSS optimization, inlining it. 
If you use useHead it would be a link and you'd have to make an HTTP request for the style sheet.
Stick to the CSS option, unless you need some sort of async script, that is not essential for your app you can use useHead for it.

## Beyond Static: Building with Nuxt 3 and Nitro {#nuxt-3-nitro}

In Nuxt 3, it is possible to create fully hybrid sites. Which have individual route rules, which enable different rendering strategies for different sections of your website.

To explore that we'll create a little blog site and see what that might be like to deploy.

If you want to start a new project. It's recommended to go to [nuxt.new](https://nuxt.new){:target="_blank rel="noreferrer"}
There are a couple of templates there, but some interesting things are coming soon.

[You can follow the Nuxt official installation Docs](https://nuxt.com/docs/getting-started/installation){:target="_blank rel="noreferrer"}

Open a terminal and run `npx nuxi init appName`

```shell
npm install
```

```shell
npm i zod @picocss/pico
```


`app.vue` -- is the entry point to our app.

`nuxt.config.ts` -- No need to do anything here, for now.

`nuxt.json` -- has nuxt as a dev dependency and the dependencies we just installed should be automatically added

`tsconfig.json` -- is going to enable our editor IDE to know a little bit about the Nuxt environment, it's running in.


Start the dev server
```shell
npm run dev -- -o
```

Add a `<script>` tag to the `app.vue` file

and import the `@picocss/pico` dependency.
It will add some styles to the app. That is going to make it a little bit nicer.

```vue
<!-- app.vue -->

<template>
  <div>
    <NuxtWelcome />
  </div>
</template>

<script setup lang="ts">
import "@picocss/pico"
</script>
```

- Add navigation to `app.vue`
	- `<NuxtLink>`  is a drop in replacement for an `<a>` link.
- Replace the `<NuxtWelcome />` with `<NuxtPage />`
	- `<NuxtPage />`  component is going to render whatever the active route is. 

```vue
<!-- app.vue -->

<template>
	<main class="container">
		<nav>
			<ul>
				<li><NuxtLink to="/">Home</NuxtLink></li>
				<li><NuxtLink to="/about">About</NuxtLink></li>
			</ul>
		</nav>
		<div>
			<NuxtPage />
		</div>
	</main>
</template>

<script setup lang="ts">
import "@picocss/pico"
</script>
```

- Create a `pages` directory in the root folder.
- Create an `/pages/index.vue` and `pages/about.vue` pages
- Fetch some Json placeholder inside the `pages/index.vue` page.


```vue
<!-- pages/index.vue-->

<script setup lagn="ts">
// using the fetch API
const posts = await fetch('https://jasonplaceholder.typicode.com/posts')
	.then((response) => response.json())
</script>
```

```js
<!-- pages/index.vue-->

<script setup lang="ts">
// Using Nuxt $fetch is the same, but abstracts away some of the boilerplate code
const posts = await $fetch('https://jasonplaceholder.typicode.com/posts')
</script>
```

```js
<!-- pages/index.vue-->

<script setup lang="ts">
// The above is going to make the data get fetched on the server and also on the client.
// Because it's running directly in the script setup.
// Nuxt provides a composable called useFetch, which prevents that.
// It also gives some other useful helper functions and utils, it will give us an error object, to tell us if an error has happened, ...
// The key benefit is it plays well with server and client

const { data: posts } = await useFetch(
	'https://jasonplaceholder.typicode.com/posts'
)
</script>
```

- We can use a transform hook in the useFetch options, to validate the response, by creating a new schema inline, an array of posts, then parsing the data, it's going to force us to know if something is going wrong and throw an error. Also, it's going to provide a nicely typed response to have access to things like `post.id` in the template.

```vue
<!-- pages/index.vue-->

<script setup lang="ts">
const { data: posts } = await useFetch(
	'https://jasonplaceholder.typicode.com/posts', {
	transform: data=> z.array(postSchema).parse(data)
})
</script>

<template>
</template>

```

- Generate a `postSchema` using Zod.

```vue
<!-- pages/index.vue-->

<script setup lang="ts">
import { z } from 'zod'

// generate a schema to specify the type of the post you want to generate
// Zod helps with schema generation. To specify the type of the post we want to validate.
const postSchema = z.object({
  id: z.number(),
  title: z.string(),
  body: z.string(),
  userId: z.number(),
})

// Fetch json placeholder data
const { data: posts } = await useFetch(
  'https://jsonplaceholder.typicode.com/posts', {
    transform: data=> z.array(postSchema).parse(data)
  })
</script>

```

- Loop over the posts and render them on the page.

```vue
<!-- pages/index.vue-->

<script setup lang="ts">
import { z } from 'zod'

// generate a schema to specify the type of the post you want to generate
// Zod helps with schema generation. To specify the type of the post we want to validate.
const postSchema = z.object({
  id: z.number(),
  title: z.string(),
  body: z.string(),
  userId: z.number(),
})

// Fetch json placeholder data
const { data: posts } = await useFetch(
  'https://jsonplaceholder.typicode.com/posts', {
    transform: data=> z.array(postSchema).parse(data)
  })
</script>

<template>
 <div>
   <h1>Blog Posts</h1>
   <article v-for="post in posts" :key="post.id" >
    <header><strong>{{ post.body }}</strong></header>
    <p></p>
    <NuxtLink :to="`/posts/${post.id}`">Read more &raquo;</NuxtLink>
   </article>
 </div> 
</template>

```

- Update the `app.vue` page.
		- `<NuxtPage />` will 

```vue
<template>
  <main class="container">
    <nav>
      <ul>
        <li><NuxtLink to="/">Home</NuxtLink></li>
        <li><NuxtLink to="/about">About</NuxtLink></li>
      </ul>
    </nav>
    <div>
      <NuxtPage />
    </div>
  </main>
</template>
 <script setup lang="ts">
import "@picocss/pico"
</script>
```

- Run a dev server `$ npm run dev` and check the result.

![Posts/Landing page with a list of posts and a link to each](/assets/i/nuxt-nation-2022/nuxt-blog-posts.png)

- Create `/pages/posts/[id].vue`

```vue
<script setup lang="ts">
import { z } from 'zod'

// generate a schema to specify the type of the post you want to generate
// Zod helps with schema generation. To specify the type of the post we want to validate.
const postSchema = z.object({
  id: z.number(),
  title: z.string(),
  body: z.string(),
  userId: z.number(),
})

// Grab the post's id from the current route
const id = useRoute().params.id
// Fetch json placeholder data of this particular post
const { data: post } = await useFetch(
  `https://jsonplaceholder.typicode.com/posts/${id}`, 
  {
    transform: data=> postSchema.parse(data)
  }
  )
  // Handle the possibility of the post object being null
  if (!post.value) {
    throw createError({
      statusCode: 404,
      message: 'Post not found'
    })
  }

</script>

<template>
 <div>
   <h1>{{ post.title }}</h1>
    <p>
      {{ post.body }}
    </p>
    <NuxtLink to="/">Back Home</NuxtLink>
 </div> 
</template>

```

Here's the result when clicking on a post.

 ![Post page with a title and body and a "Back Home" button](/assets/i/nuxt-nation-2022/nuxt-blog-post.png)

![404 page with "Post not found" text](/assets/i/nuxt-nation-2022/404-nuxt-page.png)

Finally to deploy we might want to have some configurable rules at `nuxt.config.ts`.

```ts
// nuxt.config.ts

export default defineNuxtConfig({
	routeRules: {
		// my about page is going to be static. I don't want to revalidate that page. It's complete. Once it's rendered, once. It can be saved in a CDN somewhere and used to render the following responses.
		'/about': { static: true },
		// But the posts page I might want to be revalidated. So we can turn it on still while we revalidate, and then every 60 seconds this will be refreshed, if necessary. 	
		'/posts/*': { swr: 60}
	}
})
```

We can also create a server API route `server/api/test.ts`

```ts
// server/api/test.ts

export default defineEventHandler(async event => {
	return { foo: 'bar'}
})
```

We might make this accessible to other apps and turn on cors mode in this case at `nuxt.config.ts`

```ts
// nuxt.config.ts

export default defineNuxtConfig({
	routeRules: {
		'/about': { static: true },
		'/posts/*': { swr: 60},
		'/api/test': { cors: true }
	}
})
```

Turn off the dev server `$ ctrl c`
If you run `npm build` a node server will be built for you. If you deploy it to any hosting service, Vercel, Netlify, Cloudflare Pages, ... Nuxt will try and detect the environment and create the right kind of build.

If you want to test it locally you can pass the NITRO_PRESET environment variable or just configure it in `nuxt.config` 

```shell
NITRO_PRESET=netlify npm run build
```

Everything is going to be put into a single folder that can be deployed. Any needed dependency will also be located in this folder, so it will not need to be installed again. Normally it's a `.output` folder, but in this case, it's a `.netlify` folder.

There's also a `dist` folder which will have all the things that Netlify is going to the server from CDN. This will also include `_headers` and `_redirects` files which will configure Netlify to use builder functions.

![.netlify folder prepared for deploying to Netlify](/assets/i/nuxt-nation-2022/deploy-nuxt-to-netlify-directory.png)


Deploying the output to Netlify will give you a URL to test it on. Using the link we can visit the site and see it working as expected.

In the terminal, we can have a look at the headers for requests

```shell
http URL_from_Netlify
```

If we fetch the home page, every time we fetch it's a new request, a newly rendered page (Age=0)

For the about page, the first fetch request is the `age=0`, but on subsequent requests, it keeps going up. Because it's never going to be generated again it's a fully static page. The same is true for posts pages.

It means that you don't need to redeploy when you change the content of CMS if you're using hybrid rendering.

## Tools To Explore {#tools}

- [Docus](https://docus.dev/){:target="_blank rel="noreferrer"} -- Create your own Docs with Nuxt.
- Nuxt typography
- Nuxt Studio (still in Beta)
- [Vuetelescope.com](https://www.vuetelescope.com/){:target="_blank rel="noreferrer"}
- [sidebase.io](https://sidebase.io/){:target="_blank rel="noreferrer"} -- An auth module
- [Nuxt (3) Module Builder](https://github.com/nuxt/module-builder){:target="_blank rel="noreferrer"}
- [Vue storefronts](https://vuestorefront.io/){:target="_blank rel="noreferrer"}
- [Strapi](https://strapi.io){:target="_blank rel="noreferrer"}