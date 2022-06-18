---
title: Learn Figma By Making A Card Component
layout: post
author: Mostafa Lotfy
section: Design
permalink: /design/figma-negative-stack-card-component-in-5steps/
description: How to use Figma's interactive components to easily make a dropdown menu.
---

![2 Figma components made up of negatively stacked cards presented inside a MacBook](/assets/i/v15/figma-negative-stacked-card-component-indieDev-mstflotfy.png)

In this article, I want to show you how I used **auto layout** and **components** to recreate the pin stack you see above (from the Pinterest design) in Figma.

I broke this down into 12 mini-steps:

1. [Grab screenshots to have quick in-page references.](#screenshot)
2. [Inspect Pinterest's code to get precise measurements for the design elements.](#inspect)
3. [Install the Unsplash plugin and add add an image.](#unsplash)
4. [Set the image properties](#image-properties)
5. [Add an auto-layout frame (a container for the images)](#images-container)
6. [Add 2 text boxes and set their properties](#text)
7. [Turn it into a component](#component)
8. [Add text component properties](#text-prop)
9. [Add an icon (boolean) component property](#bool-prop)
10. [Take instances of the component](#instances)
11. [Add a hover variant](#hover-variant)
12. [Present and test the design](#present)

<small>
	You can also watch it on [YouTube](https://www.youtube.com/c/mstflotfyindieDev){:target="_blank rel="noreferrer"}. A video for this article will be published soon.
</small>

<small>
	[Here's the final Figma file](https://www.figma.com/community/file/1119848425895842486){:target="_blank" rel="noreferrer"}.
</small>

## 1 Take Screenshots For Reference {#screenshot}

I'm making a **Pinterest Clone in Figma** as an exercise to to work on developing an eye for good **Ui & Ux**. ([Check out my Pinterest Clone In Figma playlist](https://www.youtube.com/playlist?list=PLsOexrcoU3Q4b-dI6chgagDntDD-AgetO){:target="_blank rel="noreferrer"}) 

So, I started by heading to the Pinterest website and grabbing screenshots of the parts of the design I am going to copy.

<small>If you're using a Mac you can take a screenshot by pressing <kbd>cmd shift 4</kbd>, then select the area you want in your screenshot. A neat trick I recently learned is pressing and holding the <kbd>ctrl</kbd> key while making the selection and the image will be copied to your clipboard. Then you can head to Figma and just press <kbd>cmd v</kbd> and you're done! </small>

![2 screenshots of multiple cards with text below them, inside a Figma file. ](/assets/i/v15/pinterest-component-screenshots.png)

Open a **new Figma draft** design file, and **paste** the screenshots. 

We have **2 card stacks** that are almost identical except that they have **different text** and one has a **lock icon** above it. 

The second screenshot shows the **hover state**. It's hard to see in the screenshot but there is a **subtle difference on hover** that makes the card stack just a tiny **bit darker**.

## 2 Inspect Code For Precise Measurements {#inspect}

Since this is just an exercise you can size elements just by eying them, which I always do for exercises. But I found it **insightful** to dig in and have a look at the **actual sizes** of the elements.

![right clicking on the card stack and selecting Inspect from the menu](/assets/i/v15/inspect-image.png)

All you need to do is head to your browser, **right-click**, and select **"Inspect"**

![Page is split between code and Pinterest's board page](/assets/i/v15/inspect-code.png)

**Code** will appear next to the page (which might seem intimidating if you're not used to code, but we're **just grabbing some measurements**).

Press on the **"select an element in the page to inspect it"** icon. 

![Label above image that shows size](/assets/i/v15/inspect-image-size.png)

**Hover** above the **first image** in the stack and its **size** will show up **above it (116px * 155px)**.

![css code showing the image has a border-radius of 16px](/assets/i/v15/inspect-border-radius.png)

The code on the right side shows us 2 things; **elements** and **style**. 

Elements (the code above) is the **HTML**; the structure of the page; the elements the page is made up from. The HTML you see here is all the HTML for this page.

Style (the code below) is the **CSS** (the style and looks of the elements on the page). The CSS you see below the HTML is only the style of the HTML element you select. So **to find the style of an element you must select it first**.

We already know the dimensions of the image, now we want to know the **corner radius**. In **CSS** corner radius is called **border-radius**.

We can manually look through the CSS code and look for border-radius, but there's too much CSS code. Above the CSS code, there's a **filter** text box. Write radius or border-radius in it. 

It might show no result! Even though it clearly has a border radius!

You'll see inside the HTML code many lines that start with `<div`. You can think of a **div** as a Figma frame. It wraps around and holds other elements, including other frames or divs. So the corner radius might not be applied to the element directly but to another frame that is holding it.

So keep selecting the line above in the HTML code until your filter gives you a result. Just going a couple of **divs** up will show you the value of the border-radius property (`border-radius: 16px;`).

![Pinterest's board page. image stack's code is selected and its dimension are shown (236*157px)](/assets/i/v15/inspect-stack-properties.png)

Keep going upwards through the divs in the code till the stack of images only is highlighted and get its width and height. The dimensions will pop up above it when you select its code. **(236 * 137 px)**

![whole component code inspected](/assets/i/v15/inspect-component-properties.png)

Then get the width and height of the **full component(236 * 215 px)**.

![Main text inspected](/assets/i/v15/inspect-h2-text-properties.png)

Finally, select the main text and get its **font size (20px)**.

![inspector open and hovering above text](/assets/i/v15/inspect-.png)

And the font size of the secondary text **(12px)**.

![hovering above icon while the inspector is open and dimensions are shown](/assets/i/v15/inspect-icon-size.png)

One last thing we need to grab is the dimensions of the lock icon (**32 * 32 px**).

![Inspector code on the right page on the left drop-down open with devices to select from](/assets/i/v15/toggle-device-inside-inspector.png)

<small>
	If you're wondering about the point of getting precise measurements when the sizes will change when the device size changes, they won't.
</small>

<small>
	The way Pinterest handles responsiveness is they keep the elements' sizes the same but the grid holding the elements changes. More elements are added horizontally when the size increases and elements are removed when the device's width gets smaller. 
</small>

<small>
	You can see this if you open the toggle device toolbar and change to a smaller device, all the sizes we took are the same, even the text! but the grid adapts by presenting fewer columns
</small>

## 3 Grab An Image From Unsplash {#unsplash}

We need an image to work with so grab one from **Unsplash**. 

Instead of going to [Unsplash.com](https://unsplash.com/){:target="_blank" rel="noreferrer"} searching for an image, downloading it, uploading it into Figma, then doing this for all the other images we'll need later, just [install the Unsplash Figma plugin](https://www.figma.com/community/plugin/738454987945972471/Unsplash){:target="_blank" rel="noreferrer"}.


![a search bar over the Figma canvas with Unsplash written in it](/assets/i/v15/open-unsplash-in-figma.png)

To quickly open the Unsplash plugin (or any other plugin), get the quick access menu by pressing <kbd>cmd /</kbd> or <kbd>cmd p</kbd> (probably "ctrl p" for windows), write **Unsplash** and press enter, and it will open.

![Unsplash plugin hovering above figma's canvas and image dropped inside the canvas](/assets/i/v15/image-from-unsplash-in-figma.png)

Select any image and it will be dropped into your canvas.

## 4 Set Image Properties {#image-properties}

![Image zoomed-in, given rounded corners, width, and height](/assets/i/v15/image-width-height-radius.png)

Select the image and give it the dimensions we grabbed from the inspector earlier; a width of <kbd>116px</kbd> and a height of <kbd>155px</kbd>. And give it a <kbd>16px</kbd> corner radius.

## 5 Auto Layout Frame (Images Container) {#images-container}

According to our in-page reference (the screenshot), we want to have 4 images stacked on top of each other.

We'll start by adding an auto-layout frame around our image, this frame will be the container for all 4 images.

![image wrapped in an auto-layout frame](/assets/i/v15/add-auto-layout-frame.png)

Select our image and press <kbd>Shift A</kbd>, this will add an **Auto layout** frame around it. 

I renamed this auto-layout frame to **"images"** to keep the layers panel organized and readable.

<small>
	When using Figma forget about using rectangles and putting elements inside them (just like you would with a classic graphic design app). Figma has a tool for wrapping other elements called frames. A frame is like a container for your elements, a bit like an HTML **div** element. For example, a webpage can be a frame with 3 frames inside it; header, main, and footer. The header has a home button, this can be a frame as well, and so on. 
</small>

<small>
	There are 2 types of frames in Figma; regular frames and auto-layout frames. Regular frames allow you to layout the elements inside it freely, while auto-layout frames have more specific values to manage the alignment of the elements inside it. This speeds up your workflow for the majority of cases where elements are laid out in an ordered manner. So use auto-layout frames whenever possible.
</small>

![auto layout padding removed. Frame wrapping around the image with no extra padding.](/assets/i/v15/remove-auto-layout-padding.png)

The auto-layout frame has padding by default, so remove it, by setting All paddings to <kbd>0px</kbd>.

![4 images inside an auto-layout frame](/assets/i/v15/add-images-to-auto-layout-frame.png)

To add the other 3 images select the image inside the auto layout frame, and press <kbd>cmd c</kbd> then press <kbd>cmd v</kbd> 3 times. Our auto-layout frame is set in the horizontal direction so the images will be next to each other, just what we want.

![Upnsplash plugin open and image changed](/assets/i/v15/change-images-from-unsplash.png)

Bring up the Unsplash plugin again, and change the images. Select the image you want to replace in the design, and once you click on an image in the Unsplash plugin it will replace it.

![4 different images stacked on top of each other](/assets/i/v15/negative-stacked-images-auto-layout.png)

To make the images stack on top of one another, set the distance between them to a negative number. 

The width we took from the inspector for the image container is **236px**, so keep reducing the **Spacing between items** property until the width of the whole frame is exactly **236px**.

![image stacked on top of one another first on top from the left](/assets/i/v15/change-stack-order.png)

The order of our images is wrong, the last image is on top. We want the first to be on top.

Press on the 3-dotted icon, in the **Design** panel, in the Auto layout settings section, to go to **auto-layout advanced settings**. And change the **Canvas stacking** to **"First on top"**.

![Zoom in on card stack reference shows a white border around images](/assets/i/v15/pinterest-boards-image-border.png)

Also, our image stack is a bit hard to look at, as nothing separates the images. 

Looking back at the reference you can see that each image has a white border around it.

![image CSS shows a solid white border of 1px](/assets/i/v15/border-around-image.png)

Inspecting the code again, I found a property of the image that we missed. It has a 1px white border around it.

![4 negatively stacked images inside Figma each with a solid white stroke of 1px.](/assets/i/v15/add-stroke-to-image.png)

To select all 4 images at the same time, select the **"images"** frame and press <kbd>Enter</kbd>. At the design panel, go to strokes and press on the **+** icon next to it to add a stroke around each image. Give it a white color. The default size is one pixel already.

## 6 Add Text To Your Component {#text}

We grabbed the font size from the inspector earlier, but not the font weight so I went back in and got it. 

![inspecting the main text code in Pinterest shows a font-weight property that has a value of bold.](/assets/i/v15/inspect-main-text-font-weight.png)

The font-weight for the main text is bold.

![inspecting secondary text show it has a value of normal](/assets/i/v15/inspect-secondary-font-weight.png)

And the font weight for the secondary text is normal/regular.

![2 text box added in Figma under the image stack, but not in a frame with it. The main text is bold with 20px. Secondary text is regular with 12px. Both use a Roboto font.](/assets/i/v15/add-text-in-figma.png)

Add 2 text boxes and set the **"main text (All Pins)"** to <kbd>20px</kbd>, <kbd>Roboto</kbd>, <kbd>bold</kbd>, and the **"secondary text"** to <kbd>Roboto</kbd>, <kbd>12px</kbd>, <kbd>regular</kbd>.

<small>
	To add a text box press on the <kbd>T</kbd> key to grab the text tool, then press on the canvas and a text box will be added.
</small>

![Pinterest boards page with code inspector open. The div holding the text is highlighted and its dimensions are "236*50"](/assets/i/v15/inspect-div-holding-text.png)

In Figma, we'll group the 2 text boxes, by adding an auto-layout frame around them. 

In the code, the same thing is happening the main and secondary texts are grouped inside an HTML div element. 

I found this element and inspected its code to see what properties this frame will have. It has an 8px padding in all directions (top, bottom, right, and left).

Also, the text's div/frame has a height of 59px.


![2 text boxes inside an auto-layout frame, aligned left, with 8px padding.](/assets/i/v15/auto-layout-all-text.png)

Select the 2 text boxes then press "Shift A" to add an **auto-layout** frame around them. 

In the design panel, under **auto-layout** settings, give the frame a padding of "8px". Then change the "distance between items" till the height of the frame is 59px.

I named this frame "text" to keep the layers panel organized.

![auto-layout frame around cards frame and text frame, with no padding, and a height of 215px](/assets/i/v15/add-auto-layout-to-component.png)

Then to wrap everything in a frame I select the **images frame** and the **text frame** and press <kbd>Shift A</kbd> to add another **auto layout** frame around everything. And name it <kbd>card</kbd>.

Also, adjust the **distance between items** inside the **card frame** till the height of it is <kbd>215px</kbd>.

## 7 Create a component {#component}

We'll turn the card into a component, this will allow us to take many instances of it. And if we update our component all the instances will be updated. 

By turning the card into a component we can also make a hover variant for it and prototype our component.

![card is selected and hovering above Create component button](/assets/i/v15/turn-auto-layout-frame-to-component.png)

To turn the **card frame** into a **component** select it and press the **create component** button at the top of the page.

![mouse hovering above the component icon in the layers panel, while the new component is selected.](/assets/i/v15/show-frame-as-component.png)

Notice how the **icon of the frame** changed to the **component icon** in the **layers panel** and also to a **purple color** to make it distinct from normal elements.

## 8 Text Component Properties {#text-prop}

Next, we'll add **component properties**. We'll start by adding **text component properties**. 

**Component properties** are a part of [**Figma's new update (config 2022)**](/design/figma-new-update-2022/). Using them makes **customizing instances** of your components easier and faster, and will allow you to **use fewer variants**.

![All pin (main text) is selected and mouse hovering above Apply text property icon in the Design panel.](/assets/i/v15/add-text-component-property.png)

To set a **component property**, **select** the **element** you want to turn into a **customizable/editable property**, in this case it's the **main text (All Pins)**. 

In the **design panel**, next to **content**, press on the **Apply text property** icon.

![Create component property pops up above the page. property is named: Text, with a value of All Pins. Mouse-hovering above the "create property" button.](/assets/i/v15/name-text-component-property.png)

You'll be prompted to give your new **component property** a **Name** and a **default Value**, after you do, click on **Create property**.

![secondary text (1, 851 Pins) is selected, create text property icon is clicked, a drop-down menu is shown, and pointer hovering above create property](/assets/i/v15/second-text-component-prperty.png)

And the **same** goes for the **secondary text (1,851 Pins)**. 

## 9 Add A Boolean Property To Show/Hide An Icon {#bool-prop}

Normally I just quickly grab icons from one of the icons plugins in Figma, but I couldn't find this one. So instead of searching for it online, or recreating it in Figma, I just went to the icon in Pinterest and grabbed its SVG code.

<small>
	[SVG](https://developer.mozilla.org/en-US/docs/Web/SVG){:target="_blank rel="noreferrer"} stands for scalable vector graphics. It's used to display vector graphics for the web.
</small>

![Pinterest boards page is shown. Code inspector is open on the right. SVG icon is selected to be copied.](/assets/i/v15/copy-icon-svg.png)

Go to **Pinterest's boards page** and **right-click** on the **lock icon** and select **inspect**. The SVG HTML tag of the icon should be highlighted. **Copy it** by pressing <kbd>Cmd/Ctrl C</kbd>.

![svg icon pasted in Figma under the card component](/assets/i/v15/paste-icon-svg-in-figma.png)

Paste it inside your Figma File by pressing <kbd>cmd/ctrl v</kbd>.

![svg icon's frame turned into an auto-layout, and width and height are set to **fixed**.](/assets/i/v15/turn-icon-frame-to-auto-layout.png)

Leave the width and height of the vector as they are. 

We want the **frame** around the vector to have a **rounded white fill**. 

So I turn the frame around the icon into an **auto-layout frame** by selecting it and pressing **<kbd>shift A</kbd>**, setting the icon resizing to **fixed horizontally and vertically**, so its size won't change when we resize the frame. 

You can also select the icon and set its **constraints** to center and center then you won't need to turn the frame into an auto-layout frame.

<small>
	To easily select all the items inside a frame (a regular frame or an auto-layout frame), select the frame and press <kbd>Enter</kbd>. In our case, by selecting the frame of the icon and pressing <kbd>Enter</kbd>, we can quickly select and edit the vector inside it.
</small>

![Lock icon selected](/assets/i/v15/allign-icon-to-center.png)

Change the frame's width and height to <kbd>32px</kbd> (The size we got for the icon earlier). Then set it to **center alignment**, to center the vector inside it.

![lock icon with white circular background](/assets/i/v15/give-icon-frame-layer.png)

Give the icon's frame a fill and rounded corners.

To add a fill press on the **+** icon next to **Fill** inside the **Design panel**, and set the color to white.

In the **design panel**, **Frame**, give the frame a <kbd>100px</kdbd> rounded corners, to turn it into a circle.

![lock icon inside the image stack frame and selected](/assets/i/v15/add-lock-icon-to-image-stack.png)

Drop the icon into our component inside the **"images frame"**. It will go next to the images and push them out of place. We want it to be above the images.

![Lock icon above the image stack and cursor hovering above absolute position.](/assets/i/v15/give-icon-relative-position.png)

We'll easily make it hover above the images inside the "images frame" by selecting it and pressing on the new Figma feature **absolute position** inside the Frame setting in the design panel. 

<small>
	Absolute position is a part of Figma's latest update. It allows an element to be a part of an auto-layout frame, but we can set it freely with a fixed position inside the frame. So it's still grouped with the elements of its frame but it doesn't need to follow its positioning and alignment rules.
</small>

![`margin-left: 16px;`](/assets/i/v15/inspect-icon-frame-code.png)

![`margin-top: 16px;`](/assets/i/v15/icon-frame-margin-top.png)

To get a precise position for the icon inside the card frame I went back and inspected the code and found that it has a margin-left of 16px, and a margin-top of 16px.

![icon above image stack with 16 px top and left between it and the frame](/assets/i/v15/align-icon-in-frame.png)

Translating this in Figma, just give the element an x and y positions of <kbd>16px</kbd> inside the images frame.

![icon selected and cursor hovering above Add boolean property icon](/assets/i/v15/add-boolean-property-in-figma.png)

Now to create a component property to toggle this image on and off in our instances, select the icon, and inside the design panel, next to "Layer" press on the **create boolean property icon**.

<small>
	Boolean properties are used to show and hide any layer inside your component.
</small>

![Create component property box pops above page to name property](/assets/i/v15/name-icon-boolean-property.png)

And, you'll be prompted to  give your new property a name and value. 

I set it to False (hidden) by default, but it doesn't matter much.

![frame tool selected and cursor hovering above Macbookpro 14" in the design panel.](/assets/i/v15/add-a-macbook-frame.png)

## 10 Take Instances Of The Component {#instances}
Let's try out our component properties.

We'll start by adding a frame. This frame will be the container for our design. It represents the webpage where the design is viewed.

To present a design it must be inside a frame. I selected a Macbook pro 14'' as the size of the frame but you can select any other device or make a custom size, it doesn't matter much in our case.

![2 instances of the component in a mac frame](/assets/i/v15/put-instances-in-frame.png)

Drop 2 instances of our component inside the MacBook frame. 

To take an instance of a component just make a copy of it, the fastest way is to just grab it while pressing and holding the <kbd>alt</kbd> key and drop the instances inside our Macbook frame.

![the second instance selected and component properties updated](/assets/i/v15/change-instance-properties.png)

The first instance on the left is exactly how we want it to be, so select the second one. Inside the design panel, you'll see that the component properties we set are there with their default values. 

Now you can edit the component easily. 

Just toggle the icon on, and change the values of "Text" and "Text2" to match our design.

![component is selected and the cursor is hovering above the create component icon.](/assets/i/v15/add-variant.png)

## 11 Add A Hover Variant {#hover-variant}
To add a hover state to our button, we need to create a new variant. 

Component properties don't work in prototypes, and we want the hover property to work in the prototype so we must use a variant in this case.

Select the card component and press on the **Add variant** icon at the top of the page.

![New variant is selected. Property 2 is renamed to hover and it is set to True.](/assets/i/v15/set-variant-property.png)

Both variants have one property, named "property 1", by default. 

In the first variant its value is set to "Default" and for the new variant it's set to "Variant 2". 

![default variant is selected and its hover property is set to False](/assets/i/v15/set-default-variant-property.png)

So We'll change the name of "property 1" to **<kbd>hover</kbd>** and we'll set the default variant to <kbd>False</kbd> and for variant 2 we'll set it to <kbd>True</kbd>. 

![another image was added to the stack increasing the width.](/assets/i/v15/duplicate-image.png)

We want an element to cover the "images frame" that will act as our hover effect.

So duplicate one of the images by selecting it and pressing <kbd>cmd c</kbd> then <kbd>cmd v</kbd>.

The new image will be added next to the images, just like the icon did.

![image on top of image stack is set to absolute position](/assets/i/v15/absolute-position-image.png)

To fix this and make it above them, give it an **absolute position** inside the "images frame".

![Image covering all image stack.](/assets/i/v15/fill-frame-image.png)

Then manually resize it to cover the whole "images frame".

![rectangle is selected. Fill is set to solid color with 21%](/assets/i/v15/change-image-to-solid-fill.png)

Change its fill from image to a solid color. 

we'll just eye this one, the hover effect should just be a little bit darker. 

Give it a dark gray color and lower the opacity.

![hover=False variant is connected to hover=True variant. The design panel is switched to the Prototype panel. The interaction is open and set to while hovering change to hover.](assets/i/v15/figma-interactive-components-hover.png)

Finally for this to work inside a prototype switch to the prototype panel (<kbd>Shift E</kbd>). 

Grab the node next to the "hover =false" variant and connect it to "hover=true". 

The "interaction details" will pop up, change it from "on click" to "while hovering".

![hover variant toggled on and off](/assets/i/v15/figma-component-properties.png)

You can check the hover effect inside the canvas as well, by selecting an instance and toggling the hover variant "on".

The effect is above the icon, in our design, the icon shouldn't be affected by hover.

![icon frame is selected inside hover variant. x and y positions are both set to 16px.](/assets/i/v15/mstflotfy-design-figma-boolean-property.png)

To fix this get back to the "hover=True" variant and in the "layer panel" grab the icon's frame and put it above the hover effect's frame.

## 12 Present It {#present}
Finally, select the "MacBook frame" and present it by pressing the play button at the top left side of the page, above the design panel.

![2 instances presented pointer above one of them shows hover effect](/assets/i/v15/figma-frame-presented.png)

Hover above our cards and you should see the hover effect.

It's a bit darker than the subtle effect we want.

![rectangle's (hover) opacity 6%](/assets/i/v15/mstflotfy-indieDev-adjust-hover-opacity-again.png)

Get back and reduce the opacity and check again. 

![2 image instances are presented, hovering above the first shows a very subtle change in color just like Pinterest.](/assets/i/v15/mstflotfy-indieDev-design-figma-present-frame.png)

I'm hovering above the one on the left and there's just the slightest difference, which matches our design.

And finally, we're done! Here's a full view of our final design file.

![full Figma design page is shown with references, components, and frame to present.](/assets/i/v15/mstflotfy-indieDev-figma-design.png)

[Here's the final Figma file](https://www.figma.com/community/file/1119848425895842486){:target="_blank" rel="noreferrer"}.

**Thanks for reading!**

## Other Articles you might want to read:
- [Figma (Config 2022) New Updates](/design/figma-new-update-2022/)
- [3 Steps To Make A Figma Dropdown Menu](/design/figma-dropdown-3steps/)
