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
    
    .. rubric:: Text message Response

    Use this response to send text messages.

    .. rubric::

            {
                messages : [
                    {
                        message: {
                            text: "Hello Botme"
                        }
                    }
                ]
            }

    .. rubric:: Sending images
    
    Use this response to send image files. Messenger supports JPG, PNG and GIF images. If you are having issues with GIF rendering, 
    please try to reduce the file size.
    
    .. rubric::

        {
            messages : [
                {
                    messaging_type: "RESPONSE",
                    message: {
                        attachment: {
                            type: "template",
                            payload: {
                                template_type: "media",
                                elements: [
                                    {
                                        media_type: "image",
                                        url: "https://picsum.photos/200/300"
                                    }
                                ]
                            }
                        }
                    }
                }
            ]
        }

    .. rubric:: Text with buttons response 
    
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
                                        "payload": "{\"payload\":\"<BUTTON_PAYLOAD>\",\"botId\":<BOT_ID>,\"value\":\"English\",\"next_pack\":\"<UNIQU_PACK_IDENTIFIER>\",\"button_type\":\"post_back\",\"button_id\":\"BUTTON_ID\"}"
                                    },
                                    {
                                        "title": "العربية",
                                        "type": "postback",
                                        "payload": "{\"payload\":\"<BUTTON_PAYLOAD>\",\"botId\":<BOT_ID>,\"value\":\"\\u0627\\u0644\\u0639\\u0631\\u0628\\u064a\\u0629\",\"next_pack\":\"<UNIQU_PACK_IDENTIFIER>\",\"button_type\":\"post_back\",\"button_id\":\"<BUTTON_ID>\"}"
                                    }
                                ]
                            }
                        }
                    }
                }
            ]
        }

        Sending images
