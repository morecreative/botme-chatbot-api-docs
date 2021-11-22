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

    .. image:: _static/images/json/text_message.*

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

    .. image:: _static/images/json/typing_message.*

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

    .. image:: _static/images/json/text_with_button.*

    .. code-block::

        {
            "messages": [
                {
                    "message": {
                        "attachment": {
                        "type": "template",
                        "payload": {
                                "template_type": "button",
                                "text": "Three button type url, phone, postback",
                                "buttons": [
                                    {
                                        "title": "go to botme.com",
                                        "type": "web_url",
                                        "url": "http://botme.com"
                                    },
                                    {
                                        "title": "call 911",
                                        "type": "phone_number",
                                        "payload": "+2911"
                                    },
                                    {
                                        "title": "Go to pack test",
                                        "type": "postback",
                                        "payload": {
                                            "payload": "go to pack <PACK_HASH>",
                                            "botId": <BOT_ID>,
                                            "value": "Go to pack test",
                                            "next_pack": "<PACK_ID>",
                                            "button_type": "post_back",
                                            "button_id": "<BUTON_ID>"
                                        }
                                    }
                                ]
                            }
                        }
                    }
                }
            ]
        }
    
    You have three button types
    
    - ``web_url`` to make the button goes to external url
    - ``phone_number`` will open the dialing panel on your device
    - ``postback`` for more information `webhook <json_plugin.html#postback-response>`_


    .. rubric:: Sending images
    
    Use this response to send image files. Messenger supports JPG, PNG and GIF images. If you are having issues with GIF rendering, 
    please try to reduce the file size.
    
    .. image:: _static/images/json/image_message.*

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

    .. image:: _static/images/json/gallary_message.*

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

    .. image:: https://scontent.fcai19-4.fna.fbcdn.net/v/t39.2365-6/21274842_1998857677000635_328116182651502592_n.png?_nc_cat=111&ccb=1-5&_nc_sid=ad8a9d&_nc_aid=0&_nc_ohc=LdXpccXStCcAX-BFUHn&_nc_ht=scontent.fcai19-4.fna&oh=08e475c665f0011a564654414c7226b1&oe=61A1703B
        :width: 200

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

    .. image:: _static/images/json/quick_reply.*

    .. code-block::

        {
            "messages": [
                {
                    "messaging_type": "RESPONSE",
                    "message": {
                        "text": "test quick reply",
                        "quick_replies": [
                            {
                                "content_type": "text",
                                "title": "Go to pack test",
                                "payload": {
                                    "payload": {
                                        "type": "quick_reply",
                                        "key": "<QUICK_REPLY_KEY>",
                                        "custom_attribute": null,
                                        "value": "Go to pack test"
                                    },
                                    "next_pack":"<QUICK_REPLY_NEXT_PACK>",
                                    "button_type":"quick_reply",
                                    "button_id":"<QUICK_REPLY_BUTTON_ID>"
                                }
                            }
                        ]
                    }
                }
            ]
        }

    Please contact the support at ``hello@botme.com`` to guide you throw how to get these values ``<QUICK_REPLY_KEY>``, ``<QUICK_REPLY_NEXT_PACK>``, ``<QUICK_REPLY_BUTTON_ID>``
        
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

Postback response
==================

You can use this button type to make the conversation go to customized pack on the buildmode at `botme.com <https://www.botme.com>`_.

.. code-block::

    {
        "messages": [
            {
                "message": {
                    "attachment": {
                    "type": "template",
                    "payload": {
                            "template_type": "button",
                            "text": "Postback button type postback",
                            "buttons": [
                                {
                                    "title": "Go to pack test",
                                    "type": "postback",
                                    "payload": {
                                        "payload": "go to pack <PACK_HASH>",
                                        "botId": <BOT_ID>,
                                        "value": "Go to pack test",
                                        "next_pack": "<PACK_ID>",
                                        "button_type": "post_back",
                                        "button_id": "<BUTON_ID>"
                                    }
                                }
                            ]
                        }
                    }
                }
            }
        ]
    }

Please contact the support at ``hello@botme.com`` to guide you throw how to get these values ``<PACK_HASH>``, ``<BOT_ID>``, ``<PACK_ID>``, ``<BUTON_ID>`` 