---
title: "Using localStorage to persist unsaved sessions in my Nuxt app"
layout: post
author: Mostafa Lotfy
section: Dev
permalink: /dev/persist-state-localStorage-OneExercise
description: 
image: /assets/i/v20/persist-session-localStorage-nuxt-1xercise.png
---

<br>

Hey, I'm building my indie apps and sharing some of the lessons I come across on [my website](/) and my YT channel: [The indieDev](https://www.youtube.com/@theindiedev.mstflotfy){:target="blank" rel="noopener"}.

## [OneExercise Workout Tracker](https://oneexercise.mstflotfy.com){:target="blank" rel="noopener"}

I finally built my first App: [OneExercise (1Xercise)](https://oneexercise.mstflotfy.com/){:target="blank" rel="noopener"}: A free workout tracker that runs in your browser and gives you instant colored feedback by comparing the current workout to the very last one. I am still fixing some bugs and rethinking the design and functionality to improve the UX. 

![Screenshot showing OneExercise (1Xercise) app's side menu with the current version Beta](/assets/i/v20/OneExercise-workout-tracker-dark-mode.jpg)

But, it's very functional. I've been using it for the past 3+ months to track my own workouts. 

![Screenshot showing 1Xercise app's stats page, and showing the period I've been using the app to track my workouts (period: 113 days)](/assets/i/v20/OneExercise-workout-tracker-stats.jpg)

In the following video, I talk about one of the latest issues I found while using my NuxtJs app, [OneExercise (1Xercise)](https://oneexercise.mstflotfy.com/){:target="blank" rel="noopener"}, and how I used [`localStorage`](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage){:target="blank" rel="noopener"} to fix it.

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/HNquoFO4Y2c?si=Z2uKAJIbakbQsHRD" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


Here are some quick notes from the video:

## The Problem: Losing unsaved session state on page reloads and app closures

I came across an issue while using [OneExercise](https://oneexercise.mstflotfy.com){:target="_blank" rel="noopener"}, where I was losing my running (unsaved) workout session whenever the page is reloaded or the app is closed. This was especially painful whenever I was tracking a workout that has a timer (like a 'Dead Hang' or a 'Power walk' workout)

I mainly use [OneExercise](https://oneexercise.mstflotfy.com){:target="_blank" rel="noopener"} as a PWA downloaded by the Chrome browser on my Android phone. Whenever I switch to another app temporarily, the Chrome browser tends to restart the app, resulting in a very bad experience and losing unsaved progress.

## Different ways to save data in the browser

There are many ways to save data in the browser. ([This article shows 10 different ways to save data in the browser]( https://www.sitepoint.com/client-side-storage-options-comparison/){:target="_blank" rel="noopener"}.)

I had already been using **indexedDb** to store [**OneExercise**](https://oneexercise.mstflotfy.com){:target="_blank" rel="noopener"} users' workouts & exercises in the browser via Dexie.Js. [**Dexie.Js**](https://dexie.org/){:target="_blank" rel="noopener"} is a wrapper library that simplifies working with **indexedDb** that I use in OneExercise. However, indexedDb is more suitable for storing a large amount of structured data and is an overkill for what I needed to do, which is to temporarily store a very small amount of data (the current user's unsaved workout info), in the browser.

I looked into **sessionStorage**, but sessionStorage would only save state across page reloads, if the app is closed the data will be lost. 

I found localStorage to be the most suitable solution; it stores state across page reloads and even when the app is closed.


## How To Use localStorage

The following code example shows how simple it is to use localStorage to quickly save state in the browser.

```javascript
// Saving each item separately in localStorage as a string

let workoutName = 'Sprints'

localStorage.setItem('unsavedWorkoutName', workoutName)
workoutName = localStorage.getItem('unsavedWorkoutName')

// clean up
localStorage.removeItem('unsavedWorkoutName')

```

```javascript
// Saving related items as one object in localStorage

let workout = {
	name: 'Walk',
	date: new Date()
}

localStorage.setItem('unsavedWorkout', JSON.stringify(workout))

// update workout val
workout = JSON.parse(localStorage.getItem('unsavedWorkout'))

// clean up
localStorage.removeItem('unsavedWorkout')
```

## How I used localStorage in my Nuxt.js app 1Xercise

I created this [simple GitHub repo](https://github.com/mstflotfy/Nuxt.js-isolated-localStorage-persistent-session){:target="_blank" rel="noopener"} to show how I persist unsaved workout sessions in OneExercise.

When a user adds/edits a workout, I watch the values of the current unsaved workout session, if they are changed, I save the changes into localStorage.

```vue
<script setup lang="ts">
// ...

// Save to localStorage
watch([workoutName, workoutDate], ([newName, newDate], [oldName, oldDate]) => {
			localStorage.setItem('unsavedWorkoutName', newName)
			localStorage.setItem('unsavedWorkoutDate', newDate)
			localStorage.setItem('unsavedId', workoutId as string)
})

// ...
</script>
```

Then, whenever the page is reloaded, I check if there is an unsaved session in localStorage, if I find one I load it.

```vue

<script lang="ts" setup>

	// ...

  onMounted(() => {
    // Load from localStorage
    const unsavedId = localStorage.getItem('unsavedId') ?? ''
    const unsavedName = localStorage.getItem('unsavedWorkoutName') ?? ''
    const unsavedDate = localStorage.getItem('unsavedWorkoutDate') ?? ''
    if (unsavedId) {
        workoutName.value = unsavedName
        workoutDate.value = unsavedDate
    }
  })  

	// ...
</script>
```

Finally, when the user presses navigates back, I remove the workout session from localStorage:

```vue
<script lang="ts" setup>

	// ...

  onBeforeRouteLeave(() => {
    // Reset localStorage
    localStorage.removeItem('unsavedId')
    localStorage.removeItem('unsavedWorkoutName')
    localStorage.removeItem('unsavedWorkoutDate')
  })
</script>
```

If the app is closed, the user will first visit the root page. So I check if there is already an unsaved running workout session in localStorage, if yes I direct the user towards it using the ID I saved in localStorage, if not I just direct the user to the workout page as the normal entry point of the user journey.

```vue
<script lang="ts" setup>
  const router = useRouter();

  onMounted(() => {
    const unsavedId = localStorage.getItem('unsavedId') ?? ''

    if (unsavedId) {
      router.push(`/workouts/${unsavedId}`);
    } else {
      router.push('/workouts')
    }
  })
</script>
```

Checkout the full code at the [GitHub repo](https://github.com/mstflotfy/Nuxt.js-isolated-localStorage-persistent-session){:target="_blank" rel="noopener"}, or the [video](https://youtu.be/HNquoFO4Y2c){:target="_blank" rel="noopener"} for more details.

## Links from this post
- [Persist session Using localStorage In Nuxt.Js, GitHub Repo](https://github.com/mstflotfy/Nuxt.js-isolated-localStorage-persistent-session){:target="_blank" rel="noopener"}
- [Use localStorage to keep unsaved Sessions Running , Youtube Video](https://youtu.be/HNquoFO4Y2c){:target="_blank" rel="noopener"}

- [MDN Docs, Using the Web Storage API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API){:target="_blank" rel="noopener"}

- [MDN Docs, Client-side storage](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Client-side_storage){:target="_blank" rel="noopener"}

- [Article, 10 Client-side Storage Options and When to Use Them](https://www.sitepoint.com/client-side-storage-options-comparison/){:target="_blank" rel="noopener"}

- [Nuxt.js Official Docs](https://nuxt.com/docs/getting-started/installation){:target="_blank" rel="noopener"}

## Other Posts You Might Find Interesting
- [How I coded my website's Figma design](/design/figma-to-code-html-css)
- [5 Lessons from Wire-framing My First App](/design/first-wireframe-5lessons-7step-workflow)

#nuxtjs  #localstorage  #1xercise #oneexercise #indiedev #mstflotfy #webdevelopment