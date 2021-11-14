=============
Message Types
=============

.. note::

    Make sure you put the correct values for `<BOT_ID>, <CID>, <SENDER_ID>, <GETSTARTED_PACK_ID> </requirements.html>`_

Text With Buttons
=============
the response is a message with two buttons like in the image below remember you will use each button payload 
to build the new payload to the same `webhook`_ request

.. note::

    Make sure to save <UNIQU_PACK_IDENTIFIER> to use in the request if the user want to click on this button

.. _webhook: /webhook.html

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
                                    "payload": "{\"payload\":\"english60800f1a573a9\",\"botId\":<BOT_ID>,\"value\":\"English\",\"next_pack\":\"<UNIQU_PACK_IDENTIFIER>\",\"button_type\":\"post_back\",\"button_id\":\"5f9ee977e7757f294855e063\"}"
                                },
                                {
                                    "title": "العربية",
                                    "type": "postback",
                                    "payload": "{\"payload\":\"\\u0627\\u0644\\u0639\\u0631\\u0628\\u064a\\u062960800f1a574cc\",\"botId\":<BOT_ID>,\"value\":\"\\u0627\\u0644\\u0639\\u0631\\u0628\\u064a\\u0629\",\"next_pack\":\"<UNIQU_PACK_IDENTIFIER>\",\"button_type\":\"post_back\",\"button_id\":\"5f9ee977e7757f294855e064\"}"
                                }
                            ]
                        }
                    }
                },
                "typing": 0
            }
        ]
    }

Text With Quick Replies
=============
the response is a text message with two quick replies like in the image below.

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
                            "payload": "{\"payload\":{\"type\":\"quick_reply\",\"key\":\"<QUICK_REPLY_KEY>\",\"custom_attribute\":null,\"value\":\"Orders List\"},\"next_pack\":\"<UNIQU_PACK_IDENTIFIER>\",\"button_type\":\"quick_reply\",\"button_id\":\"61911e51467180331c5dfe02\"}"
                        },
                        {
                            "content_type": "text",
                            "title": "Tickets List",
                            "payload": "{\"payload\":{\"type\":\"quick_reply\",\"key\":\"<QUICK_REPLY_KEY>\",\"custom_attribute\":null,\"value\":\"Tickets List\"},\"next_pack\":\"<UNIQU_PACK_IDENTIFIER>\",\"button_type\":\"quick_reply\",\"button_id\":\"61911e51467180331c5dfe03\"}"
                        }
                    ]
                },
                "typing": 0
            }
        ]
    }