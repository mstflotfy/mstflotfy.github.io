---
title: Figma New Updates (2022)
layout: post
author: Mostafa Lotfy
section: Design
permalink: /design/figma-new-update-2022/
description: A Quick look at Figma's new updates. And how to use the new features, using brief practical examples. 
---

## Outline
<small>You can come back to the outline by pressing the back button of your browser.</small>

- [Intro](#intro)
- [Dark Mode](#dark-mode)
- [Variable Fonts](#variable_fonts)
- [Auto Layout Text Baseline Alignment](#baseline)
- [Auto Layout Visual Alignment](#visual)
- [Individual Strokes](#individual-strokes)
- [Component Properties](#component-properties)
- [Auto Layout Negative Spacing](#negative-spacing)
- [Spring Animation](#spring-animation)
- [Favoriting Files](#favorites)

## Intro {#intro} 
![what's new in Figma at Figma config 2022](/assets/i/v14/what's_new_in_figma.png)

Figma just had a new update a couple of days ago (actually about 2 weeks ago). In this article, I'll go through most of the new features using brief practical examples. 

The update includes many little changes, but the main 2 upgrades came to auto-layout and components. And since auto-layout and components are the main features of Figma, it's important to understand these updates and how to use them to improve your workflow.

There is no better way to explain something than to use an example. So let's have a look at the updates by creating a button.


<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/AZg1oGWn6SY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
Here's [a link to the Figma community file](https://www.figma.com/community/file/1111642615512042772){:target="blank" rel="noreferrer"} used in this article.

## Dark Mode {#dark-mode}

![Dark mode in Figma came to Figma](/assets/i/v14/dark_mode.png)

We'll start by opening a new design file. 

![Create a new design file in Figma](/assets/i/v14/new_file.png)

And the first new feature is Dark-mode. The easiest way to toggle between dark and light modes is to press "Cmd /" to open up "Quick actions", then write "dark", and press enter. The Ui changes to Dark-mode but the Canvas's color we have to change ourselves. This makes sense, if Figma changes it for you, the color it chooses might conflict with your design. To change the color of the Canvas (The background color), click anywhere on it, then at the Design panel, adjust the "Background" color. 

![Use the quick access menu to toggle dark mode](/assets/i/v14/quick_dark.png)

![change canvas background color](/assets/i/v14/dark_background.png)

## Variable Fonts {#variable_fonts}

![Now you can use Variable fonts in Figma](/assets/i/v14/variable_fonts.png)

Let's make our button.

Grab the text tool (T), press to insert a text box, and write "Button", then change the font to "Roboto Flex". 

![Create a text box](/assets/i/v14/button.png)

Figma just added support for variable fonts. 

I also didn't know what variable fonts were when I first read this.

I didn't dive deep into it but here's what I understood by reading briefly on it; Basically variable fonts give you more flexibility while customizing your type, instead of just preset custom sizes and styles (like "Bold", or "italic"), variable fonts give you more control. At the same time, all this functionality is packed in one file (unlike normal fonts, where each style has a new file), this leads to faster load times.

If you want to read more on variable fonts, check out this [Introduction to variable fonts on the web](https://web.dev/variable-fonts/){:target="blank" rel="noreferrer"} article. 

Just note that not all fonts are variable fonts, and not all variable fonts give you the same amount of options. "Roboto flex" gives many options so you can play with it and customize it.

To access the variable options select the text, go to the design panel, Text, click on "Type settings" (The three dots icon), then select the variable tab. And you can start customizing the text of your button.

![Adjust variable fonts inside your Figma design](/assets/i/v14/adjust_font.png)

## Auto Layout Text Baseline Alignment {#baseline}
Now let's add an auto-layout frame around our text. Which will function as the frame for our button. Do this by selecting the text and then pressing "Shift A". You can also name the frame "button".

![Add an auto-layout frame around your text](/assets/i/v14/button_autolayout.png)

We also want our button to have an icon, next to the text. To do this press "cmd /" and then write the name of any icon plugin you have installed, I used the "Material Design Icons" plugin. If you don't have one you can install one from the [Figma community](https://www.figma.com/community){:target="blank" rel="noreferrer"}. 

Just select some random icons that you might want to use for your button. I'll turn each of those icons into a component by individually selecting each icon, and pressing the create component button at the very top of the page. Then I will group these components by selecting all of them and adding an auto-layout frame around them, giving this frame a stroke and naming it "buttons_icons".

![Frame the icons to use with our auto-layout button](/assets/i/v14/buttons_icons.png)

Grab an instance (just a copy) of one of the icons components, and drop it into the button. (The auto-layout frame holding the text)

A new feature added to auto-layout is text-based alignment, to use it select the button's auto-layout frame, in the design panel, auto-layout, press on "Advanced auto-layout settings". Then press on the checkmark next to "text-based alignment". This should align the icon and text to the bottom, regardless of the text's line-height. (This, however, adjusts the text to the frame holding the icon, so if there is space between the icon and its, frame it will not give you the desired result.)

![auto layout text baseline alignment example](/assets/i/v14/Pasted%20image%2020220521205639.png)

## Auto Layout Visual Alignment {#visual}
Auto-layout now has visual alignment added to it. So we can visually adjust the padding and the spacing between items.

![You can now align elements visually inside auto-layout frames in Figma](/assets/i/v14/Pasted%20image%2020220521205806.png)

## Individual Strokes {#individual-strokes}

Let's add a stroke to our button. (In the design panel, Stroke, press the plus button.)

Another new feature in Figma is individual strokes. Inside the stroke settings, you'll find a circle icon, if you hover above it should say "Strokes per side", click on it, and choose left. 

Now, we have a stroke to one side only. Bump up the size of the stroke to 10px. 

You can also press on the "Strokes per side" icon, and have complete control over stoke size per side.

![How to add individual strokes to your elements in Figma](/assets/i/v14/Pasted%20image%2020220521210229.png)

We've covered a lot of updates, but now let's move to the big one.

## Component Properties {#component-properties}

![component properties in Figma](/assets/i/v14/Pasted%20image%2020220521234327.png)

Select our button frame, and turn it into a component by pressing the "Create component" button, at the top of the page.

![Create a button component in Figma](/assets/i/v14/Pasted%20image%2020220521234018.png)

We can still use components the same way we're used to, by creating variants, and variant properties, but we now have the option of using component properties as well.

Components properties are different than variant properties. A component property can be a boolean property (allows you to toggle a layer on and off), a text property (allows you to quickly change the default text, without needing to manually select text boxes), or an instance swap (allows you to easily swap nested components). This will only make sense with an example.

Select the text inside our button, by double-clicking. Then inside the design panel, you'll find a new content section, you can edit the default text here, then press on the "Apply text property" icon. Leave the property name as text, and its default value as "Button". and click on "Create property".

![How to create a text component property in Figma](/assets/i/v14/Pasted%20image%2020220521235311.png)

Now take an instance of our button component (You take an instance just by copying it). You can notice the difference between a component and its instance by noticing its icons. Any changes you make to the component will automatically take place in all its instances.

![Create an instance of your button component](/assets/i/v14/Pasted%20image%2020220521235617.png)

Select the instance and now you can change the text to any text you want right from the design panel, no need to select the text box anymore. This saves time, especially when your design is complex, and it would take many clicks to get to your text boxes.

Since I have a fingerprint icon, I'll change the text to unlock.

![Update your text using text component property](/assets/i/v14/Pasted%20image%2020220521235836.png)

Let's add secondary text to our button. In the component, duplicate the "Button" text box. Change the new text to a smaller and thinner size. We want it to be below the main text. But our auto-layout is set in the horizontal direction, so we'll select both text boxes and press "Shift A" to add a nested auto-layout frame around them, and set it in the vertical direction. Update the line height, set them to left alignment, and set the spacing between them. 

![Add a nested auto-layout frame to your component](/assets/i/v14/Pasted%20image%2020220522000631.png)

Select the new smaller text and create a new text property for it. Since we duplicated the other text box and it has a "Text" property this one does too, but we want it to have a new property. So inside the design panel, content, press on "Remove property", change the text, then press on the "Apply text property" icon, then select "Create new property", name it "secondary_text" and press "Create property". 

![Remove component property](/assets/i/v14/Pasted%20image%2020220522000854.png)

![Add a new text component property](/assets/i/v14/Pasted%20image%2020220522001011.png)

Now, if you select our instance you'll have 2 options, Text and Secondary_text. So set a custom secondary_text.

![Update your button's text using text component properties](/assets/i/v14/Pasted%20image%2020220522001159.png)

Now that we have 2 text boxes, text baseline alignment is not ideal, so remove it and align to center instead.

![Remove text baseline alignment](/assets/i/v14/Pasted%20image%2020220522001321.png)

Let's add a boolean property. Select the icon in our component. And go to the design panel, Layer, then press on the "Apply boolean property icon". Name the property whatever you want, I'll name it "icon", and leave it set to true.

![How to add a boolean property in Figma](/assets/i/v14/Pasted%20image%2020220522001708.png)

Grab another instance of our button. Select it and have a look at the design panel. You'll find a new option in there to toggle the icon off and on. Toggle it off. Not all buttons will have icons. This will allow you to use one component in different cases. Change the text properties. 

![Toggle an icon on and off using boolean properties in Figma](/assets/i/v14/Pasted%20image%2020220522002235.png)

But if we want a button with no secondary text? We'll just add a new boolean property that will toggle the secondary text on and off.

Select the secondary text inside the button component. In the design panel, Layer, press on the "Add boolean property" icon.Then "create property", name it "show_secondary_text", and leave it as True. 

![Add a boolean property to your button](/assets/i/v14/Pasted%20image%2020220522104457.png)

Make a new instance, and toggle the secondary text off. I framed the instances together in an auto-layout frame to separate them from the component, and later in this article, we'll present this frame when we make the buttons interactive.

![Toggle layer using a boolean property](/assets/i/v14/Pasted%20image%2020220522105434.png)

We also want to easily switch between the icons that we chose for our design, so let's create an instance swap property. 

Select the icon inside the component. And in the design panel, next to the name of the component, press on "Apply instance swap property". Name the property "select_icon" And press "Create property". 

![Apply an instance swap property](/assets/i/v14/Pasted%20image%2020220522112119.png)

Now create a fourth instance of our button component. And inside the design panel, find the select icon property and you'll find a drop-down menu that allows you to swap easily between the icons inside our "buttons_icons" frame, change the text to go along with your new icon, and remove the secondary text.

![Swap between components using an instance swap property](/assets/i/v14/Pasted%20image%2020220522112417.png)

Component properties allowed us to use one component to make four different button styles.

But when to avoid using a component property and use a variant instead?

I think it's best to set your properties first, then create variants if needed. You can set properties after creating variants, but this will require setting them to every variant, which will add a bit of work, not too much but why do more work than needed.

The first case where you don't want to use a component property and should use a variant instead is if you want to use interactive components (if you want to create an interaction, between different variants), like creating a hover state, that will work in prototypes, for example. Component properties can't be used interactively inside prototypes. interactive components work by internally connecting variants of the same components together, so obviously you need a variant to do this. 

So let's create a hover state for our button. Select our button component. The add "Add variant" button moved from the design panel to the top of the page. I read some frustrated comments about this, but it makes little difference. Press on the button and a new variant will be added.

![How to add a new variant in Figma after the update](/assets/i/v14/Pasted%20image%2020220522120759.png)

![Add a new variant](/assets/i/v14/Pasted%20image%2020220522120901.png)

Variants have properties. No two variants can have the exact same property values, if they do, you'll get an error message. By default the first variants you create will have one property, named "Property 1", and its value will be "Default" for the very first variant, and "Variant 2" for the new variant. Let's change this to something that makes more sense. Change "Property 1" to "Hover", change "Default" to "False", and "Variant 2" to "True".

![Change variant's property name and value](/assets/i/v14/Pasted%20image%2020220522121015.png)

Now let's change the looks of the "Hover=True" variant so that when we change to it we actually see a change. Select the "Hover=True" variant, add a fill to it, and give it any color you want your hover effect to be. We can change the text style as well.

![How to add a hover variant in Figma](/assets/i/v14/Pasted%20image%2020220522131157.png)

Now let's select our instances and we can toggle the hover on and off. Everything is working fine, except I think we've discovered a bug. When the instance with the icon swapped changes to hover, the icon gets stuck with the hover color! 

![Toggle between your variants](/assets/i/v14/Pasted%20image%2020220522131405.png)

![Switch between your Figma variants](/assets/i/v14/Pasted%20image%2020220522131433.png)

I've sent to Figma's team about this bug, hopefully, it will be fixed.

To make this work in a prototype select the "Hover=False" component, press "Shift E" to switch to prototype settings, and connect it to the "Hover=True" variant, with a "While hovering" and "change to" connection. 

![Use interactive components to create a hover effect](/assets/i/v14/Pasted%20image%2020220522132022.png)

To present the design and try out the prototype. Select the "Instances" frame, give it a fill, then press the present button.

![Present your frame in Figma](/assets/i/v14/Pasted%20image%2020220522134650.png)

Now you can hover above all the buttons and see the hover effect in action.

![button hover prototype in Figma](/assets/i/v14/Pasted%20image%2020220522134806.png)

Now let's look at some of the other new Figma updates, that we didn't cover in our example.


## Auto Layout Negative Spacing {#negative-spacing}

We've mentioned some changes to auto-layout while going through the previous example. We mentioned visual spacing and text baseline alignment, but the more impactful changes are negative spacing and relative positioning.

Auto-layout now allows negative spacing and this allows you to stack elements on top of each other. In an upcoming article, I'll show you how I used it to create the example below.

![Using the new auto-layout negative spacing to recreate Pinterest's pins stack](/assets/i/v14/Pasted%20image%2020220522141144.png)

For now, just know that it's there. And to use it just set the distance between elements to a negative number, and you can choose the order of the stack from the advanced auto-layout settings.

![Figma's auto-layout negative spacing practical example](/assets/i/v14/Pasted%20image%2020220522142032.png)

The order of the stack can be reversed, by going to "Advanced layout settings" and setting "Canvas stacking" to "First on top".

![Using canvas stacking in Figma](/assets/i/v14/Pasted%20image%2020220522143750.png)

And here's another bug. An element that is in a negative stack does not know the difference between hovering over it or over the element above it. I assume the same issue would be there with clicking as well. In the image below I hover above the unlock button, but in the common area between it and the Dev button and both buttons are showing the hover effect.

![Discovered a Figma negative stacking bug](/assets/i/v14/Pasted%20image%2020220522143506.png)


## Spring Animation {#spring-animation}

![Introduction to Spring Animations In Figma](/assets/i/v14/Pasted%20image%2020220522145434.png)

Select one of your icons and add a variant to it. You can rename "Property 1" to "clicked", and give it a value of "True" instead of "Variant 2". Change the "clicked=Default" variant to "clicked=False".

![Add a new variant and name its property](/assets/i/v14/Pasted%20image%2020220522162900.png)

Switch to prototype settings by pressing "Shift E", and connect the "clicked=False" variant to "clicked=True". Set the connection interaction to "on click" and "change to". Change the instant animation to "smart animate". Then select one of the preset spring animations (Gentle, Quick, Bouncy, or Slow) or make a custom one.

![Set a spring animation in Figma](/assets/i/v14/Pasted%20image%2020220522163538.png)

For an animation to actually happen there should be a difference between the 2 variants. So bump up the size of the second variant a bit, and let's also change its color.

![Change the size and color of the variant for the spring animation to take place](/assets/i/v14/Pasted%20image%2020220522164609.png)

To present it make a new frame and add an instance of the "clicked=False" variant inside it, then present the frame and try it out.

![present frame to check the spring animation](/assets/i/v14/Pasted%20image%2020220522164930.png)

The icon will change to the larger size using a spring animation. 

It would be nice if it would change back to its original size after a short delay. So, go back to the component, select the "clicked=True" icon variant, press "Shift E" to switch to prototype settings, and set an "After delay" of "800ms", "change to", "clicked=False" interaction to it.

![Make a delayed animation in Figma](/assets/i/v14/Pasted%20image%2020220522201628.png)

Present the frame and click try it one more time.

![Present your design](/assets/i/v14/Pasted%20image%2020220522201939.png)

Check the prototype it should change to clicked=True, then after a short delay, change back to clicked=False.

![spring animation with a delay](/assets/i/v14/spring_animation.gif)

## Favoriting Files {#favorites}

The drafts folder will become a mess once you have a large number of files in there. There is no way to organize files. And it becomes more and more difficult to find older files as the number of files in your drafts folders grows. Finally, Figma added the ability to add files to a Favorites list, this is not enough to end the mess, but it's a good first step.

You can add a file to the "Favorite files" list in the drafts folder by right-clicking it and selecting "Add to your favorites" or pressing on the star icon. 

![Add a file to your Favorites list in Figma's Drafts folder](/assets/i/v14/Pasted%20image%2020220522221057.png)

You can also add a file to your Favorites while you're inside the file.

![add a file to Favorites](/assets/i/v14/Pasted%20image%2020220522221239.png)

---

This is it. These are the updates I found most impactful and for a full official list check [this page](https://www.figma.com/whats-new/){:target="blank" rel="noreferrer"}. You can also check the free Figma community file with the examples in this article. 

You might want to check out this article: [How to make a dropdown menu in Figma](/design/figma-dropdown-3steps/).