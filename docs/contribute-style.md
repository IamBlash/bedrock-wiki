---
title: How to edit pages on our wiki
hidden: true
mentions:
    - TheItsNameless
---

## Working on the wiki

Now that you have our wiki locally, you can edit the files right on your device. If you don't know how to work with VSCode, there are some very good videos from Microsoft itself [here](https://code.visualstudio.com/docs).

To make our pages look prettier, we have a lot of great tools, that you can use to highlight sections, insert components, insert images, and much more!

Our wiki uses Markdown to provide a way of modifying the way text looks. With special Vue-Components, we can add things like buttons, spoilers or code blocks. Its also possible to use some HTML, but we only recommend this for advanced users and won't cover this in our guide.

## Page Setup

Each page consists of two parts: The Head (Front Matter) and the Body.

Inside the Head you write the most important information about your article.

```
---
title: How to contribute to our wiki
mentions:
-   TheItsNameless
---
```

| Name             | Required | Default | Note                                                                                                                                                     |
| ---------------- | -------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `title`          | Yes      | None    | The title of the page.                                                                                                                                   |
| `nav_order`      | No       | None    | The order in which the article will appear in the sidebar. Lower number will be higher. All nav_order pages will appear above pages without a nav_order. |
| `show_toc`       | No       | True    | Whether the table of contents will be generated for this page.                                                                                           |
| `show_edit_link` | No       | True    | Whether a link should be shown which leads to this page in the GitHub repository.                                                                        |
| `tags`           | No       | []      | A list of tags for the page. Some will be displayed on sidebar, such as 'guide' or 'beta'. All will be displayed in the actual page, at the top.         |
| `mentions`       | No       | []      | Add your GitHub username here so that you will always be in the contributors section if this page is moved.                                              |

The title is required, as it is the name shown in the bar on the left side. Mentions isn't needed, but it would be great if everyone knows who made the great article they are reading!

After the Head, you write the Body. The body is just your whole content. A common mistake everyone does the first time is to put the page title as a level 1 header on their page. You don't have to do this, because the title given in the Header will already be placed on top of your page.

## Viewing the Wiki locally

Its really hard to know how your article will look when its finished and published. To help with that, you can use a tool called `npm`!

In VSCode, in the top bar, click on `"Terminal"`, then on `"New Terminal"`.

The first time you view it locally, you have to type `npm install` and wait until its finished. This is just done **the first time**!

To view the wiki locally, type `npm run dev` and press enter and wait until its finished loading. It will show you this:

![](/assets/images/contribute/npm/npm_dev.png)

Hover over the part where it says `"http://localhost:3000/"` and press ctrl and left-click. Your browser will open with the wiki.

Done! Every time you change and save a file in VSCode it will automatically be updated in your browser.

## Working with Markdown

The wiki uses Markdown, a powerful text-formatting syntax. To learn more about Markdown, visit the official [Markdown Guide](https://www.markdownguide.org/basic-syntax)!

We wont teach you the whole Markdown-Language, but there are some things that you need to pay attention to!

### Linking

If you want to refer to another website, like the Microsoft Docs, you can use links.

To link something in Markdown, you can either just write out the whole link:

https://wiki.bedrock.dev

Or show some other text instead of the link:

[Click here!](https://wiki.bedrock.dev)

#### Linking to sources outside the wiki

To link to another source, just copy the whole link url (including the https-part in front of it) and paste it in the field:

```Markdown
[Click here for the official Microsoft Docs](https://docs.microsoft.com/de-de/minecraft/creator/)
```

[Click here for the official Microsoft Docs](https://docs.microsoft.com/de-de/minecraft/creator/)

#### Linking to other pages in the wiki

You can create links, that redirect you to other pages in the wiki. These are called `relative links`.

```Markdown
[Redirect to the contribute page](/contribute)
```

[Redirect to the contribute page](/contribute)

To redirect to another page, just look in the file explorer. The main folder is the `"docs"` folder. To link to a page thats directly inside this folder, you can just write `/pagename`, like `/contribute` to link to the contribute page. Every page that is inside a folder has to be accessed by writing the name of the folder, a slash, and then the page name: `/blocks/block-materials`.

:::warning
**NEVER** use absolute links to link to a page inside our wiki. Make sure you **don't** include `wiki.bedrock.dev` inside your links.
:::

## Working with Components

Our wiki uses special Vue-Components, which you can use to add things like Buttons, Spoilers, CodeBlocks, etc.

### Panel

Panels are used to inform or warn the user about some really important stuff. There are two types of Panels: `tip` and `warning`.

```HTML
:::tip
some tips here
:::

:::warning
a warning here
:::
```

:::tip
some tips here
:::

:::warning
a warning here
:::

Panels are created by typing three colons and the type of the Panel. Then you can write your content and at the end you close the Panel by typing just three colons.

### CodeHeader

CodeHeaders are used to nicely wrap codeblocks, so a user can easily copy the code inside them. You can also add some text, like a file path, so the users know exactly where to put this code.

````json
<CodeHeader>BP/blocks/example.json</CodeHeader>
```json
{
    "some": "json"
}
```
````

<CodeHeader>BP/blocks/example.json</CodeHeader>

```json
{
	"some": "json"
}
```

The filepath goes between the two HTML-Tags. Make sure to follow our [Style-Guide](/meta/style-guide) when describing filepaths:

-   If you link inside a Behavior-Pack, place `BP` in front of all other files:

✔️ `BP/blocks/example.json`

❌ `YourBehaviorPack/blocks/example.json`

-   Same for the Resource-Pack, use `RP` in front of all other files:

✔️ `RP/manifest.json`

❌ `YourResourcePack/manifest.json`

On the next line after the closing tag, you have to start a code block to use this Component, as shown in the example above.

### Button

A Button works like a link, but is more noticeable for the user.

```html
<BButton 
    link="https://wiki.bedrock.dev" 
    color=red
>your button text</BButton>
```

<BButton
link='https://wiki.bedrock.dev'
color=red

> your button text</BButton>

| Attribute | Required | Type   | Note                                                                                                            |
| --------- | -------- | ------ | --------------------------------------------------------------------------------------------------------------- |
| link      | yes      | String | Link to redirect when clicking on the Button                                                                    |
| color     | no       | String | Defines the color of the button <br> _Only accepts `red`, `green`, `blue` as values, otherwise it will be grey_ |

The text between the two HTML-Tags is the text that will appear on the button.

### Spoiler

A spoiler is a Component that can be used to hide some content, so it doesn't block the whole site.

```html
<Spoiler title="title">
    
text here

and here

</Spoiler>
```

<Spoiler title='title'>

text here

and here

</Spoiler>

| Attribute | Required | Type   | Note                              |
| --------- | -------- | ------ | --------------------------------- |
| title     | yes      | String | Will be displayed after the arrow |

The content between the two tags is the content that will be hidden.

Pay attention to the empty lines between the content and the tags! If you forget these, this component will not work!

### Label

A Label is a small icon with uppercase letters that can be used to give your articles more flair.

```html
<Label 
    name="name"
    color="green"
>label</Label>
```

<Label
name='name'
color='green'

> label</Label>

| Attribute | Required | Type   | Note                                                                                                    |
| --------- | -------- | ------ | ------------------------------------------------------------------------------------------------------- |
| name      | yes      | String | Text that will be displayed inside the box                                                              |
| color     | no       | String | Color of the box <br> _Only accepts `red`, `green`, `blue` as values, otherwise it will be transparent_ |

Don't overuse them! They look cool, but someone could really give them too much attention and forget to focus on other important parts of your article.

### FolderView

FolderViews are Components which can be used to show a setup of files, like in our [Project-Setup](/guide/project-setup) guide.

```html
<FolderView
	:paths="[

    'com.mojang/development_resource_packs/guide_RP/manifest.json',
    'com.mojang/development_resource_packs/guide_RP/pack_icon.png',
    'com.mojang/development_resource_packs/guide_RP/texts/en_US.lang',

    'com.mojang/development_behavior_packs/guide_BP/manifest.json',
    'com.mojang/development_behavior_packs/guide_RP/pack_icon.png',
    'com.mojang/development_behavior_packs/guide_RP/texts/en_US.lang',

]"
></FolderView>
```

<FolderView :paths="[

'com.mojang/development_resource_packs/guide_RP/manifest.json',
'com.mojang/development_resource_packs/guide_RP/pack_icon.png',
'com.mojang/development_resource_packs/guide_RP/texts/en_US.lang',

'com.mojang/development_behavior_packs/guide_BP/manifest.json',
'com.mojang/development_behavior_packs/guide_RP/pack_icon.png',
'com.mojang/development_behavior_packs/guide_RP/texts/en_US.lang',

]"></FolderView>

| Attribute | Required | Type                                | Note                                                                   |
| --------- | -------- | ----------------------------------- | ---------------------------------------------------------------------- |
| :paths    | yes      | String containing a List of Strings | Represents all files and folders which should appear in the FolderView |

The `:paths` Attribute is a String, that contains a List of all separate file paths. This String must be written with double quotes! Each file path must be written entirely and has to be wrapped inside single quotes.

### YouTubeEmbed

A YouTubeEmbed can be used to embed a YouTube Video in your article.

```html
<YouTubeEmbed id="dQw4w9WgXcQ" />
```

<YouTubeEmbed id='dQw4w9WgXcQ' />

| Attribute | Required | Type   | Note                       |
| --------- | -------- | ------ | -------------------------- |
| id        | yes      | String | ID of the video to display |

### WikiImage

A WikiImage is an alternative way to add an image in your article.

```html
<WikiImage
	src="assets/images/homepage/wikilogo.png"
	alt="alternative text"
	pixelated="true"
/>
```

<WikiImage 
    src='assets/images/homepage/wikilogo.png' 
    alt='alternative text' 
    pixelated=true 
/>

| Attribute | Required | Type    | Note                                                                                                                                                                                                                                                 |
| --------- | -------- | ------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| src       | yes      | String  | Image to show                                                                                                                                                                                                                                        |
| alt       | no       | String  | Text to show if the browser can't load the image. Not really important, as most modern browser support showing images.                                                                                                                               |
| pixelated | no       | Boolean | If the image should be pixelated <br> _Due to a bug, it doesn't matter if this attribute is true or false. As long as the attribute is present, the image will be pixelated. This attribute **must** be deleted so that the image is not pixelated!_ |

Unlike a markdown image, the image can be pixelated here.

### CardLink

With CardLinks you can make fancy boxes with an image and a text, which contains a link!

```html
<CardLink
	imgsrc="assets/images/homepage/wikilogo.png"
	title="title"
	link="https://google.com"
/>
```

<CardLink 
    imgsrc='assets/images/homepage/wikilogo.png' 
    title='title' 
    link='https://google.com' />

| Attribute | Required | Type   | Note                                   |
| --------- | -------- | ------ | -------------------------------------- |
| imgsrc    | yes      | String | Image to display inside the box        |
| title     | yes      | String | Title to show                          |
| link      | yes      | String | Link to redirect on clicking the title |

Don't overuse them! They look cool, but someone could really give them too much attention and forget to focus on other important parts of your article.

