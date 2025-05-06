# TinyMCE ChatGPT Plugin

<p align="center"><img src="https://github.com/the-3labs-team/tinymce-chatgpt-plugin/raw/HEAD/art/logo-tinyopen.svg" alt="Logo TinyMCE ChatGPT Plugin"></p>

[![Lint](https://github.com/The-3Labs-Team/tinymce-chatgpt-plugin/actions/workflows/lint.yml/badge.svg)](https://github.com/The-3Labs-Team/tinymce-chatgpt-plugin/actions/workflows/lint.yml)
![License](https://img.shields.io/github/license/the-3labs-team/tinymce-chatgpt-plugin)
![jsDelivr hits (GitHub)](https://img.shields.io/jsdelivr/gh/hy/The-3Labs-Team/tinymce-chatgpt-plugin?label=downloads)
[![Maintainability](https://api.codeclimate.com/v1/badges/1737eafb663973324bc8/maintainability)](https://codeclimate.com/github/The-3Labs-Team/tinymce-chatgpt-plugin/maintainability)

This plugin integrates ChatGPT (or your OpenAI compatible LLM) within TinyMCE, allowing you to generate realistic and creative text with the push of a button.

<p align="center"><img src="https://github.com/the-3labs-team/tinymce-chatgpt-plugin/raw/HEAD/art/demo.gif" alt="TinyMCE Demo Gif"></p>

To use the plugin, simply install and activate it in TinyMCE. Once activated, you will see a new "ChatGPT" button in the TinyMCE toolbar. Click this button to open a dialog box where you can enter a request to ChatGPT. ChatGPT will then generate the requested text and enter it into your editor.

ChatGPT can be used to generate a variety of text formats, including articles, blog posts, e-mails, letters, and more. It can also be used to translate languages, write different types of creative content, and answer your questions in an informative way.

ChatGPT is a powerful tool that can help you improve your productivity and the quality of your work. Try it out today!

## Features

- 🤖 OpenAI and Custom LLM OpenAI compatible
- ⚙️ Support custom prompts defined by you!
- 🧑‍🎨 Generates realistic and creative text with the push of a button
- 🧬 Can be used to generate a variety of text formats
- 🈷️ Can be used to translate languages
- 🙋 Can be used to answer your questions in an informative way

| :warning: WARNING                                                                                                                                         |
| :-------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Consider this plugin as a prototype and not suitable for production deployment at this time. Use it only in controlled environments and at your own risk. |

## Requirements

- TinyMCE 6|7 or later
- OpenAI API key ([get one here](https://openai.com))
- (Optional) Custom LLM API

## Installation

This plugin comes as an _external plugin_; however, you can download the _.js file_ and upload it to your host.

To install, simply **edit the init configuration** of your TinyMCE as follows:

```js
tinymce.init({
  // 1. Add the plugin to the list of external plugins
  external_plugins: {
    chatgpt:
      "https://cdn.jsdelivr.net/gh/The-3Labs-Team/tinymce-chatgpt-plugin@2/dist/chatgpt.js",
  },

  // 2. Configure the ChatGPT plugin
  openai: {
    api_key: "sk-yourapikeyhere", // Your OpenAI API key
    model: "gpt-3.5-turbo",
    temperature: 0.5,
    max_tokens: 150,
    prompts: [
      "Translate from English to Italian",
      "Summarize",
      "Proofread",
      "Write a blog post about",
    ],
    // Optional: Add your custom LLM
    // baseUri: "https://your-llm-endpoint.com",
  },

  // 3. Add the ChatGPT button to the toolbar
  toolbar: ["chatgpt"],
});
```

If you are using our [TinyMCE Laravel Nova Package 4](https://github.com/murdercode/Nova4-TinymceEditor) you can configure as follows:

```php
<?php

'init' => [

    // 1. Add the plugin to the list of external plugins
    'external_plugins' => [
        'chatgpt' => 'https://cdn.jsdelivr.net/gh/The-3Labs-Team/tinymce-chatgpt-plugin@2/dist/chatgpt.js'
    ],

    // 2. Configure the plugin
    'openai' => [
        'api_key' => 'sk-yourapikeyhere', // Your OpenAI API key
        'model' => 'gpt-3.5-turbo',
        'temperature' => 0.5,
        'max_tokens' => 150,
        'prompts' => [
            'Translate from English to Italian',
            'Summarize',
            'Proofread',
            'Write a blog post about',
        ],
        // Optional: Add your custom LLM
        // 'base_uri' => 'https://your-llm-endpoint.com',
    ],

],

// 3. Add the plugin to the toolbar
'toolbar' => ['chatgpt']

//...
```

### Breaking Changes from v1 to v2

- We are using the new `/chat/completions` endpoint from OpenAI
- The `model` default now must be a chat model, like `gpt-3.5-turbo`
- If you want to use the old `/completion` endpoint, you can use the `baseUri` option to set your custom LLM endpoint like `https://api.openai.com/v1/completions`

### Custom LLM

If you have a custom LLM, you can use it by setting the `baseUri` option in the configuration. The plugin will use this endpoint to generate the text.

```js
baseUri: "https://your-llm-endpoint.com"
```

Please note that the custom LLM must be OpenAI compatible and follow the same API as OpenAI.
Also, the custom LLM must be accessible from the client-side.
Check the `demo-lm-studio.html` file for an example of how to use a custom LLM.

## Sponsor

<div>  
    <a href="https://www.tomshw.it/" target="_blank" rel="noopener noreferrer">
        <img  src="https://3labs-assets.b-cdn.net/assets/logos/banner-github/toms.png" alt="Tom's Hardware - Notizie, recensioni, guide all'acquisto e approfondimenti per tutti gli appassionati di computer, smartphone, videogiochi, film, serie tv, gadget e non solo" />  
    </a>
    <a href="https://spaziogames.it/" target="_blank" rel="noopener noreferrer" >
        <img src="https://3labs-assets.b-cdn.net/assets/logos/banner-github/spazio.png" alt="Spaziogames - Tutto sul mondo dei videogiochi. Troverai tantissime anteprime, recensioni, notizie dei giochi per tutte le console, PC, iPhone e Android." />
    </a>
    <br/>
    <a href="https://cpop.it/" target="_blank" rel="noopener noreferrer" >
        <img src="https://3labs-assets.b-cdn.net/assets/logos/banner-github/cpop.png" alt="Cpop - News, recensioni, guide su fumetto, cinema & serie TV, gioco da tavolo e di ruolo e collezionismo. Tutto quello di cui hai bisogno per rimanere aggiornato sul mondo della cultura pop"/>
    </a>
    <a href="https://data4biz.com/" target="_blank" rel="noopener noreferrer" >
        <img src="https://3labs-assets.b-cdn.net/assets/logos/banner-github/d4b.png" alt="Data4Biz - Sito dedicato alla trasformazione digitale del business" />
    </a>
    <br/>
    <a href="https://soshomegarden.com/" target="_blank" rel="noopener noreferrer" >
        <img src="https://3labs-assets.b-cdn.net/assets/logos/banner-github/sos.png" alt="SOS Home & Garden - Realtà dedicata a 360 gradi ai settori della casa e del giardino." />
    </a>
    <a href="https://global.techradar.com/it-it" target="_blank" rel="noopener noreferrer" >
        <img src="https://3labs-assets.b-cdn.net/assets/logos/banner-github/techradar.png" alt="Techradar - Le ultime notizie e recensioni dal mondo della tecnologia, su computer, sistemi per la casa, gadget e altro." />
    </a>
    <br/>
    <a href="https://aibay.it/" target="_blank" rel="noopener noreferrer" >
        <img src="https://3labs-assets.b-cdn.net/assets/logos/banner-github/aibay.png" alt="Aibay - Scopri AiBay, il leader delle notizie sull'intelligenza artificiale. Resta aggiornato sulle ultime innovazioni, ricerche e tendenze del mondo AI con approfondimenti, interviste esclusive e analisi dettagliate." />
    </a>
    <a href="https://coinlabs.it/" target="_blank" rel="noopener noreferrer" >
        <img src="https://3labs-assets.b-cdn.net/assets/logos/banner-github/coinlabs.png" alt="Coinlabs - Notizie, analisi approfondite, guide e opinioni aggiornate sul mondo delle criptovalute, blockchain e finanza" />
    </a>

</div>
