---
title: Make A Figma Dropdown Menu in 3 steps
layout: post
author: Mostafa Lotfy
section: Design
permalink: /design/figma-dropdown-3steps/
description: How to use Figma's interactive components to easily make a dropdown menu.  
---

![Figma Dropdown Menu Thumbnail](/assets/i/v13/v13-Th.png)

Whatever the design you're working on, it will (most probably) have a **dropdown menu** somewhere. So, in this article, I'll attempt to simplify making a dropdown menu in Figma. As a part of my [Pinterest Clone in Figma](https://www.youtube.com/playlist?list=PLsOexrcoU3Q4b-dI6chgagDntDD-AgetO){:target="blank" rel="noreferrer"} exercise.

We'll use auto-layout, components, and variants. We'll create a prototype using [**interactive components**](https://help.figma.com/hc/en-us/articles/360061175334#Before){:target="blank" rel="noreferrer"}.

## Outline
You can come back to the outline by pressing the back button of your browser.

[1. Step 0: The Starting Point](#step0)  
[2. Step 1: Create a hover variant](#step1)  
[3. Step 2: Create Menu Items Components](#step2)  
[4. Step 3: Create a variant for the open state](#step3)  

## Step 0: The starting point {#step0}

![Starting point in the Figma community file](/assets/i/v13/startingPoint.png)

I've already been working on a **Pinterest Clone in Figma**. I started from scratch and created a design for the home page. I even made the [homepage design fully responsive with breaking points](https://www.youtube.com/watch?v=3KUZ3o0ddcE&list=PLsOexrcoU3Q4b-dI6chgagDntDD-AgetO&index=5&t=379s){:target="blank" rel="noreferrer"}. 

But, the design is not interactive. Pinterest has a lot of interactivity going on, even for a single page, but creating an interactive dropdown menu is not a bad place to start.

For this design, we're not starting from scratch. We'll build on the previous work. And focus only on the dropdown menu. 


One thing to note, where I ended with the last vids, I had a component for almost every element in the design. 

![All the components of the design at its starting point](/assets/i/v13/allComponents.png)

But for this file, I removed most of the components, to minimize the confusion, and only left the ones we'll need to work on, in the dropdown menu.

Inside the [file](https://www.figma.com/community/file/1104788393847411628){:target="blank" rel="noreferrer"}:

We have a screenshot, just as a reference. 

![Screenshot of Pinterest's dropdown menu](/assets/i/v13/screenshots.png)

Then we have the design frame, which we'll not do anything to. We'll only use it to present our prototype. 

![The frame holding the design, present it to try the prototype](/assets/i/v13/designFrame.png)

The main area is the "components" frame. The reason I frame them together is to keep the page clean and organized while keeping all the elements on one page. Again, I kept only the components we'll need to work with. 

![Starting components](/assets/i/v13/currentComponents.png)

Most people have their components on a separate page, for me, I prefer it this way, and I found it important when I was prototyping a full design, with many pages and connections.

The first component we have is the header component. An instance of it is already added to the design, which means that any changes we make to the header component will automatically take place inside the design. 

![Header component](/assets/i/v13/header.png)

If you're unfamiliar with components, you can check the "[Pinterest clone in Figma](https://www.youtube.com/playlist?list=PLsOexrcoU3Q4b-dI6chgagDntDD-AgetO){:target="blank" rel="noreferrer"}" playlist and it will get you familiar with it, another option is to watch "[How I used Figma to create a full design and prototype for my website](https://www.youtube.com/watch?v=euXzyxr_d6A){:target="blank" rel="noreferrer"}". 

The second component is the dropdown button component. There is an instance of it inside the header, this is called a nested component, when you have a component (the dropdown button), inside another component (the header). 

![Dropdown button component](/assets/i/v13/dropdownComp.png)

And since there is an instance of the header inside the design frame, any changes we make to the button will take effect inside the frame. And that's why we don't need to do anything with the design itself but present it. 

Imagine having 10 pages where the header is used, how much effort and headaches are we saving by updating the header component only without needing to make changes to every single frame! That's why you should always use components.

Finally, we have a component for the profile image. An instance of it is inside the header component, and therefore also inside the design frame.

![Profile image component](/assets/i/v13/profileImageComp.png)

Now let's get to it, and start making the dropdown menu.

To follow along I made [a Figma community file](https://www.figma.com/community/file/1104788393847411628){:target="blank" rel="noreferrer"}. Open the link while you're signed in to your Figma account, press on duplicate at the top right side of the page, and you'll have a copy of it in your drafts folder.

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/wRnz_AZXJaQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

In this article/video we'll make a Figma Dropdown menu in three steps:
1. Make A Hover state variant for the dropdown button component.
2. Create A "Menu items" component with its variants.
3. Make An open state variant for the dropdown button.

Below you'll find steps to act as a reference for those who watch the vid and want to quick way to remember the steps. Kind of the video notes. 

## Step 1: Create a hover variant {#step1}

We'll start by creating a hover variant for the dropdown button component so that when we hover above the button it changes from its normal state to the hover state.

![Dropdown button default and hover variants](/assets/i/v13/hoverVariant.png)

- Select the **Dropdown Button** component, and add a new variant.
- Change **property 1** to **State**.
- Set the value of **State** to **Hover**.

So now the **Dropdown Button** has two variants, the first is "Default", and the second is "Hover".

- Create a circle of 35px. 
- Set **Gray 2** color style to it.
- Place it inside the **Hover** component in the layers panel, then push it in place, using the arrow keys.

- Switch to the prototype panel (Shift E).
- Connect "Default" to "Hover" and set the interaction to "while hovering" and "change to", with an instant animation.

![Drop down button hover connection](/assets/i/v13/hoverProto.png)
- Select the Design frame and present it to try it out.

![dropdown button's hover state presented](/assets/i/v13/hover.png)

When you hover above the **Dropdown** button component, it should change from the "default" state to the "Hover" state.

## Step 2: Create Menu Items Components {#step2}

![The menu item component with all its variants](/assets/i/v13/menuItemsVariants.png)

We'll create a third variant (an open state), that is going to show the menu. But first, we'll create a new component for the menu items. Why?

The dropdown menu, we want to make, has different items. Each item has a hover state. One way to deal with this is to create multiple dropdown menu variants. One where no element has a hover effect, then one for each item in hover. So if we have three items, we'll make 4 menus!

By creating a component for each of those items, and utilizing interactive components, we only create one dropdown menu.

If this makes no sense, keep on reading, and it will.

Also, the same elements which are inside the menu are used in other places in the Pinterest design, so by creating a component for them we only need to set them once and use them everywhere.

Also, the same element is repeated multiple times in the menu, why create it multiple times? And when we decide to update it we'll have to select the same element in different places, bad business!

Therefore we'll first create the menu items, then in the next step, we'll create an open state for the dropdown button, we'll attach the menu to it and use these elements. Now we'll set each element once and use it everywhere, and also update it once when we need to, and it will update everywhere. Not just inside the menu but also in other places on the page. Not just on this page, but also on other pages when we create them!

For the Pinterest Design, we're working on we'll create 4 menu items; Title, Text, Text & link icon, and user. 

### Make A Title Variant

![Create the menu item component, starting with a text variant](/assets/i/v13/titleVariant.png)

- Grab the text tool (T), and write "Title" (Roboto, light, 20px).
- Add auto-layout to it (Shift A) (padding: 20px, 10px. Alignment: left & center)
- Turn it into a component. 
- Change its property 1 to Type=Title.

### Make A Text Variant

![Add a text variant](/assets/i/v13/textVariant.png)

-  Add a variant and change Type=Text.
- Change text to Title, Roboto, Semibold, 25px.
- Padding 20px, left & center.
- Give it rounded corners of 10 px.

- Select the frame holding both variants, and add an auto-layout frame (Shift A).
- This is optional to keep the design clean and avoid manually aligning elements. 
- Name it, "menu items".
- Select both variants, and change their horizontal resizing to "fill-container".
- Drop it inside the "Components" frame, to keep the page organized.

### Make A Text, Hover Variant

![Add a text, hover variant](/assets/i/v13/textHoverVariant.png)

- Select the Text variant, and add a new variant from it.
- Add a new property, state=Hover.
- Set the state for the above variants to state=No Hover.
- Add a fill, and give it a "Gray 2" color style.
- Switch to prototype (Shift E) and connect the Text, No Hover to the Text, Hover. Set the interaction to while hovering change to.

### A Text & link icon Variant

![Create a text & link icon variant](/assets/i/v13/textLink.png)

- Select the Text, No Hover variant. And add a new variant from it.
- Set the property: Type=Text & link icon, and the property: State= Hover.
- Open the "Feather Icons" plugin, grab a link icon, and drop it into the "Text & link icon, No Hover" variant. Change its stroke width to "3px".
- Make sure the variant's horizontal resizing is set to "fill container", and set its auto-layout alignment to "space between".

### Create a text & link hover  variant

![Create a text & link icon Hover Variant](/assets/i/v13/textLinkHoverVariant.png)

- Select the "Text & link icon" variant, and make a new variant from it.
- Set its properties. Type= Text & Link, State=Hover
- Add a fill to it, and give it the "Gray 2" color style.
- Switch to the prototype panel (Shift E)
- Select the "Text & Link, No Hover" variant and connect it to "Text & link, Hover" variant. And set the interaction to "While hovering" and "change to".

### Create the User variant

![Add another variant for the user item](/assets/i/v13/usrV.png)

- Select the "Text, No Hover" variant, and make a new variant from it.
- Set its properties; Type=User, State=No Hover.
- Edit text to "User Name"
- Duplicate the text, and change it to "Account" (Roboto, 20px, Regular), and give it a "Gray 1" color style.
- Duplicate it again, and change the text to "email".
- Select all three text boxes and give wrap them in their own auto-layout frame (Shift A) (vertical, item spacing=5px, padding=0, alignment=center & left, packed). You can name the frame user info.
- The profile image is too small. So go to the "Profile Image" component, add a new variant, give it property 1=Large, and change its size to 75px.
- Grab the profile image and drop it into the "User, No Hover" variant.
- Change the "User, No Hover" variant's auto-layout settings to a horizontal direction, 20px between items, and alignment to space between.
- Change the "User, No Hover" variant's horizontal resizing to "fill container", and vertical resizing to hug contents.
- Open the "Feather Icons" plugin, grab a checkmark icon, and drop it in the frame. And give it a stroke width of 3px.
- Set the elements inside the User variant to hug contents, except for the user info change its horizontal resizing to "fill container".

### Make a hover state for the User variant

![Add the last variant: User Hover State](/assets/i/v13/usrHv.png)

- Select the **User, No Hover** variant.
- Press on the plus button, at the button right corner of the menu items component, to make another variant of it.
- Set the properties of the new variant; "Type=User, State=Hover".
- Add a fill to the new variant.
- Give the fill a "Gray 2" color style.
- Switch to the prototype panel (Shift E)
- And connect the "User, No Hover" to the "User, Hover" variant and set the interaction to "while hovering", and "change to".
- Remove the connection the "User, Hover" has to the "Text" variant. 

## Step 3: Create a variant for the open state {#step3}
![The three drop-down button variants](/assets/i/v13/dropdownVariants.png)

### Create the open variant

![The dropdown button open variant](/assets/i/v13/openVariant.png)


- Select the **Hover variant** inside the **Dropdown Button** Component.
- Make a new variant of it.
- Set its property "state=Open".
- Switch to the prototype panel (Shift E), connect the **Hover variant** to the **open variant**, and set the connection to "On click" and "change to"
- Connect the **Open variant** to the **Default variant**, and set the interaction to "On click" and "change to".

![Dropdown button variant connections](/assets/i/v13/openConnections.png)

Now the button will start in its default state, when you hover above it, it will change to the hover variant, if you click on the hover variant it will change to the open variant, and when you click on the open variant, it will return to default again.

### Create the dropdown menu
![Three dropdown button variants for its three states](/assets/i/v13/dropdownVariants.png)
- Select one of the menu items **Title, No Hover**, and copy it to the clipboard (cmd c).
- Inside the **Dropdown Button Component**, select the **Open variant**, then paste (cmd v).
- Add an auto-layout frame around the menu item you sent (Shift A), and name it **Dropdown Menu**.
- Change horizontal resizing for the **Dropdown Menu** to Hug contents, and the menu item to "fill container".
- Manually create space for the **Dropdown Menu** inside the **Dropdown Button** component auto-layout frame. The auto-layout frame is not doing it automatically because the menu is floating outside of the frame of the **Open** variant. And from now on, manually give yourself space as needed.
- Set the auto-layout settings for the **Dropdown Menu** to vertical, "0px" between items, "10px" padding, and top & left alignment.
- Give the **Dropdown Menu** a fill, and give it the "Pinterest White" color style. And rounded corners of "10px".
- Add a "drop shadow effect" to the **Dropdown Menu**, and remove its "x" & "y" direction, and give it a "blur" of "20px"
- Then, push it in place. The button should be above its right side. (Align the dropdown button, with the dropdown menu manually.)

You might want to present the design and have a look at it.

### Add The rest of the menu items

![The dropdown menu variant](/assets/i/v13/DropdownMenu.png)

Inside the Dropdown menu frame

- Duplicate the menu item we have.
- Change the properties of the duplicate to "User, No Hover".
- If the menu is displaced, push it back in place using the arrow keys, and align it manually to the left with the dropdown button.
- You can enter details for the user to show off the design.

- Duplicate the "user, No Hover" menu item.
- Change the properties of this duplicate to "Title, No Hover"
- Change the title to "More Options".

- Duplicate The "Title, No Hover", 4 times.
- Set the first one after it to Text, No Hover, and change the text to "Settings"
- Set the next one to "Text, No Hover", and change its text to "Tune your home feed"
- Set the next one to "Text & link icon", and change its text to "Get help"
- Set the last item to "Text & link icon" and change its text to "Terms and privacy"

And we're done! Check present the design frame to check your menu.

![The Figma file after making the dropdown menu](/assets/i/v13/done.png)
In the future, when I create multiple pages, I can link those buttons inside the menu to them. For example, if I have a "Settings" page. I can link the Settings button inside the component to it, and it will work from anywhere inside the design.

![Dropdown menu in action](/assets/i/v13/donePresented.png)
