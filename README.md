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
