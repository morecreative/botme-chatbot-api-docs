=============
Message Types
=============

.. note::

    Make sure you put the correct values for `<BOT_ID>, <CID>, <SENDER_ID>, <GETSTARTED_PACK_ID> </requirements.html>`_

this requests can be one of the responses from `webhook </webhook.html>`_

Text message
=============

Text message content that the bot can reply with

.. code-block::

    {
        "messages": [
            {
                "messaging_type": "RESPONSE",
                "recipient": {
                    "id": 0
                },
                "message": {
                    "text": "content",
                    "quick_replies": []
                },
                "typing": 0
            }
        ]
    }

Text with buttons
=============
The response is a message with two buttons like in the image below, remember you will use each button payload 
to build the new payload to the same `webhook </webhook.html>`_ request

.. note::

    Make sure to save <UNIQU_PACK_IDENTIFIER> to use in the request if the user want to click on this button

.. image:: _static/images/get_started.*

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
                },
                "typing": 0
            }
        ]
    }

Text with quick replies
=============
The response is a text message with two quick replies like in the image below, remember you will use each quick-reply payload 
to build the new payload to the same `webhook </webhook.html>`_ request

.. note::

    Make sure to save <QUICK_REPLY_KEY> to use in the request if the user want to click on this quick reply


.. _webhook: /webhook.html

.. image:: _static/images/quick_replies.*

.. code-block::

    {
        "messages": [
            {
                "messaging_type": "RESPONSE",
                "recipient": {
                    "id": 0
                },
                "message": {
                    "text": "Hi and welcome",
                    "quick_replies": [
                        {
                            "content_type": "text",
                            "title": "Orders List",
                            "payload": "{\"payload\":{\"type\":\"quick_reply\",\"key\":\"<QUICK_REPLY_KEY>\",\"custom_attribute\":null,\"value\":\"Orders List\"},\"next_pack\":\"<UNIQU_PACK_IDENTIFIER>\",\"button_type\":\"quick_reply\",\"button_id\":\"<BUTTON_ID>\"}"
                        },
                        {
                            "content_type": "text",
                            "title": "Tickets List",
                            "payload": "{\"payload\":{\"type\":\"quick_reply\",\"key\":\"<QUICK_REPLY_KEY>\",\"custom_attribute\":null,\"value\":\"Tickets List\"},\"next_pack\":\"<UNIQU_PACK_IDENTIFIER>\",\"button_type\":\"quick_reply\",\"button_id\":\"<BUTTON_ID>\"}"
                        }
                    ]
                },
                "typing": 0
            }
        ]
    }

Media type
=============

This is the media type response the media can be image or video.

.. image:: _static/images/image.*

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
                            "template_type": "media",
                            "elements": [
                                {
                                    "media_type": "image",
                                    "url": "<IMAGE_URL>"
                                }
                            ]
                        }
                    }
                },
                "typing": 0
            }
        ]
    }


Carosel type
=============
The carosel card may be up to 10 cards items and the buttons on each card can be maximum 3 

.. note::

    We handle the pagination in the carosel as 10 item and the card no 11 will be the see more card

.. image:: _static/images/carosel.*

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
                            "template_type": "generic",
                            "image_aspect_ratio": "horizontal",
                            "elements": [
                                {
                                    "title": "Lion",
                                    "image_url": "<IMAGE_URL>",
                                    "subtitle": "Lion Description",
                                    "buttons": [
                                        {
                                            "title": "order",
                                            "type": "postback",
                                            "payload": "{\"payload\":\"<BUTTON_PAYLOAD>\",\"botId\":\"<BOT_ID>\",\"value\":\"order\",\"next_pack\":\"<NEXT_PACK_ID>\",\"button_type\":\"post_back\",\"button_id\":\"<BUTTON_ID>\"}"
                                        }
                                    ]
                                },
                                {
                                    "title": "Logo",
                                    "image_url": "<IMAGE_URL>",
                                    "subtitle": "Logo Description",
                                    "buttons": [
                                        {
                                            "title": "Tickets add",
                                            "type": "postback",
                                            "payload": "{\"payload\":\"<BUTTON_PAYLOAD>\",\"botId\":\"<BOT_ID>\",\"value\":\"Tickets add\",\"next_pack\":\"<NEXT_PACK_ID>\",\"button_type\":\"post_back\",\"button_id\":\"<BUTON_ID>\"}"
                                        }
                                    ]
                                }
                            ]
                        }
                    }
                },
                "typing": 0
            }
        ]
    }