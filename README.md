# TinyMCE ChatGPT Plugin
<p align="center"><img src="https://github.com/the-3labs-team/tinymce-chatgpt-plugin/raw/HEAD/art/logo-tinyopen.svg" alt="Logo TinyMCE ChatGPT Plugin"></p>

This plugin integrates ChatGPT within TinyMCE, allowing you to generate realistic and creative text with the push of a button.

<p align="center"><img src="https://github.com/the-3labs-team/tinymce-chatgpt-plugin/raw/HEAD/art/demo.gif" alt="TinyMCE Demo Gif"></p>

To use the plugin, simply install and activate it in TinyMCE. Once activated, you will see a new "ChatGPT" button in the TinyMCE toolbar. Click this button to open a dialog box where you can enter a request to ChatGPT. ChatGPT will then generate the requested text and enter it into your editor.

ChatGPT can be used to generate a variety of text formats, including articles, blog posts, e-mails, letters, and more. It can also be used to translate languages, write different types of creative content, and answer your questions in an informative way.

ChatGPT is a powerful tool that can help you improve your productivity and the quality of your work. Try it out today!

## Features

Support custom prompts defined by you!
Generates realistic and creative text with the push of a button
Can be used to generate a variety of text formats
Can be used to translate languages
Can be used to write different types of creative content
Can be used to answer your questions in an informative way
Anything what ChatGPT can handle

| :warning: WARNING          |
|:---------------------------|
| Consider this plugin as a prototype and not suitable for production deployment at this time. Use it only in controlled environments and at your own risk.     |

## Requirements

TinyMCE 6.0 or later
ChatGPT API key

## Installation

This plugin comes as an "external plugin"; however, you can download the .js file and upload it to your host.

To install, simply edit the init configuration of your TinyMCE as follows:

```php
// TODO: edit to match JS and provide also a PHP version
'init' => [

'external_plugins' => [
'chatgpt' => 'mirrorhere' 
],
'toolbar' => 'chatgpt',
'openai' => [
            'api_key' => 'sk-yourapikeyhere',
            'model' => 'text-davinci-003',
            'temperature' => 0.5,
            'max_tokens' => 150,
            'prompts' => [
                'Translate from English to Italian',
                'Summarize',
                'Proofread',
                'Write a blog post about',
            ]
        ],

]
```


