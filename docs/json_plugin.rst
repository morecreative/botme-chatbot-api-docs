=============
Json Plugin
=============
The JSON API plugin allows you to integrate your backend into your chatbots in Chatfuel.

The JSON API plugin enables your bot to send HTTP GET and POST requests and interpret responses.

**You can:**
    - Generate dynamic content.
    - Create postbacks.
    - Redirect to external URL.

**Json composer**
you can find the json composer in the build mode under ``Add Content`` Block.

.. image:: _static/images/json_composer.*

In your responses, you can: combine several messages in one answer by sending several dictionaries in the messages array.

Build your endpoint 
===================
You can find the ``JSON API`` composer on the build mode, you can choose the type of the request if 
it is ``GET`` or ``POST`` and you have the fexibility to choose a token if you want your endpoint to be secured.

also you can click on ``Add Query Param +`` button so ask the user for input from the bot 
enter the 
    ``key`` which is the message that will appear to the bot user for example (What is you orderNo?)
    
    ``value`` is key that botme will use to attach the bot user response to that key and send it to your endpoint.

so imagine you endpoint is ``/webhook/bot`` and it is available under ``GET`` method 
so your endpoint should make one of the next responses so the bot can respond to your channel(messenger, whatsapp, webbot, etc)

Response Examples
==================
    
    .. rubric:: Text message

    Use this response to send text messages.

    .. code-block::

            {
                "messages" : [
                    {
                        "message": {
                            "text": "Hello Botme"
                        }
                    }
                ]
            }

    .. rubric:: Typing message

    You can send this message to let content have a delay before displaying some messages

    .. code-block::

        {
            "messages": [
                {
                    "message": {
                        "text": "I will wait 6 seconds then send Hi"
                    }
                },
                {
                    "message": {
                        "duration": 6,
                        "type": "typing"
                    },
                },
                {
                    "message": {
                        "text": "Hi",
                    }
                }
            ]
        }

    .. rubric:: Text with buttons 
    
    Buttons on specific text  in this response type can be one of 
    .. code-block::

        {
            "messages": [
                {
                    "messaging_type": "RESPONSE",
                    "recipient": {
                        "id": 0
                    },
                    "message": {
                        "attachment": {
                        "type": "template",
                        "payload": {
                            "template_type": "button",
                            "text": "Choose your language \\ أختر اللغة ",
                            "buttons": [
                            {
                                "title": "English",
                                "type": "postback",
                                "payload": {
                                "payload": "<BUTTON_PAYLOAD>",
                                "botId": <BOT_ID>,
                                "value": "english",
                                "next_pack": "<UNIQU_PACK_IDENTIFIER>",
                                "button_type": "post_back",
                                "button_id": "<BUTTON_ID>"
                                }
                            },
                            {
                                "title": "Arabic",
                                "type": "postback",
                                "payload": {
                                "payload": "<BUTTON_PAYLOAD>",
                                "botId": <BOT_ID>,
                                "value": "arabic",
                                "next_pack": "<UNIQU_PACK_IDENTIFIER>",
                                "button_type": "post_back",
                                "button_id": "<BUTTON_ID>"
                                }
                            }
                            ]
                        }
                        }
                    }
                }
            ]
            }

    .. rubric:: Sending images
    
    Use this response to send image files. Messenger supports JPG, PNG and GIF images. If you are having issues with GIF rendering, 
    please try to reduce the file size.
    
    .. code-block::

        {
            "messages" : [
                {
                    "messaging_type": "RESPONSE",
                    "message": {
                        "attachment": {
                            "type": "template",
                            "payload": {
                                "template_type": "media",
                                "elements": [
                                    {
                                        "media_type": "image",
                                        "url": "https://picsum.photos/200/300"
                                    }
                                ]
                            }
                        }
                    }
                }
            ]
        }

    .. rubric:: Sending galleries

    Use this response to send a horizontal scrollable gallery. Each item is composed of an image attachment, short description and buttons to request input from the user.

    .. code-block::

        {
            "messages": [
                {
                "message": {
                    "attachment": {
                    "type": "template",
                    "payload": {
                        "template_type": "generic",
                        "image_aspect_ratio": "square",
                        "elements": [
                        {
                            "title": "Card #1",
                            "image_url": "https://picsum.photos/200/300",
                            "type": "element",
                            "subtitle": "Card #1 Subtitle",
                            "default_action": {
                            "type": "web_url",
                            "url": "https://botme.com",
                            "webview_height_ratio": "TALL"
                            },
                            "buttons": [
                            {
                                "title": "Visit Botme",
                                "type": "url",
                                "url": "https://botme.com",
                                "fb_type": "web_url"
                            },
                            {
                                "title": "Visit Botme shops",
                                "type": "url",
                                "url": "https://shops.botme.com",
                                "fb_type": "web_url"
                            }
                            ]
                        },
                        {
                            "title": "Card #2",
                            "image_url": "https://picsum.photos/200/300",
                            "type": "element",
                            "subtitle": "Card #2 Subtitle",
                            "default_action": {
                            "type": "web_url",
                            "url": "https://botme.com",
                            "webview_height_ratio": "TALL"
                            },
                            "buttons": [
                            {
                                "title": "Visit Botme #2",
                                "type": "url",
                                "url": "https://botme.com",
                                "fb_type": "web_url"
                            },
                            {
                                "title": "Visit Botme shops #2",
                                "type": "url",
                                "url": "https://shops.botme.com",
                                "fb_type": "web_url"
                            }
                            ]
                        }
                        ]
                    }
                    }
                }
                }
            ]
        }

    The ``image_aspect_ratio`` can be either ``square`` or ``horizontal``. Horizontal is the default.

    The ``webview_height_ratio`` ca be ``COMPACT`` or  ``TALL`` or ``FULL``

    The Gallary can be up to 10 cards usualy people use it as 9 items and the card no 10 would be for the see more items.

    .. rubric:: Sending list

    .. code-block::

        {
            "messages": [
                {
                    "messaging_type": "RESPONSE",
                    "message": {
                        "attachment": {
                        "type": "template",
                        "payload": {
                            "template_type": "list",
                            "top_element_style": "compact",
                            "elements": [
                            {
                                "title": "items",
                                "image_url": "https://botme.s3.us-east-2.amazonaws.com/97be98a71165c090f58a086c76b5b684.png",
                                "subtitle": "items subtitle",
                                "buttons": [],
                                "default_action": {
                                "type": "web_url",
                                "url": "http://botme.com"
                                }
                            },
                            {
                                "title": "item #1",
                                "image_url": "https://botme.s3.us-east-2.amazonaws.com/5debf7d574bece17d8fa45748eb4194c.png",
                                "subtitle": "item #1 subtitle",
                                "buttons": [
                                {
                                    "title": "item #1 button #1",
                                    "type": "web_url",
                                    "url": "http://shops.botme.com"
                                }
                                ],
                                "default_action": {
                                "type": "web_url",
                                "url": "http://botme.com"
                                }
                            },
                            {
                                "title": "item #2",
                                "image_url": "https://botme.s3.us-east-2.amazonaws.com/73374ff7fa208177bc50f68bfa0ff6e4.png",
                                "subtitle": "item #2subtitle",
                                "buttons": [
                                {
                                    "title": "item #2 button #1",
                                    "type": "web_url",
                                    "url": "http://shops.botme.com"
                                }
                                ],
                                "default_action": {
                                "type": "web_url",
                                "url": "http://botme.com"
                                }
                            }
                            ],
                            "buttons": []
                        }
                        }
                    },
                    "typing": 0
                }
            ]
        }

    .. rubric:: Sending quick replies

    Use this JSON to add quick replies to your responses. Quick replies are limited to 11 items per message.

    .. code-block::

        {
            messages: [
                {
                message: {
                    text: "Hello this is a text with quickreply",
                    quick_replies: [
                    {
                        content_type: "text",
                        title: "quickreply #1",
                        payload: {
                            payload: {
                            type: "quick_reply",
                            custom_attribute: null,
                            value: "quickreply #1"
                            },
                            button_type: "quick_reply",
                        }
                    },
                    {
                        content_type: "text",
                        title: "quickreply #2",
                        payload: {
                            payload: {
                                type: "quick_reply",
                                custom_attribute: null,
                                value: "quickreply #2"
                            },
                            button_type: "quick_reply"
                        }
                    }
                    ]
                }
                }
            ]
        }
        
    .. rubric:: Sending multiple messages
        
    You Can compine multiple messages but passing messages inside the ``messages`` array  

    .. code-block::

        {
            "messages" : [
                {
                    "message": {
                        "text": "Hello Botme"
                    }
                },
                {
                    "message": {
                        "text": "Hello again"
                    }
                },
                {
                    "message": {
                        "attachment": {
                            "type": "template",
                            "payload": {
                                "template_type": "media",
                                "elements": [
                                    {
                                        "media_type": "image",
                                        "url": "https://picsum.photos/200/300"
                                    }
                                ]
                            }
                        }
                    }
                }
            ]
        }