=========================
Webhook
=========================
.. note::

    Make sure you put the correct values for `<BOT_ID>, <CID>, <SENDER_ID>, <GETSTARTED_PACK_ID> </requirements.html>`_


You can use the webhook to get specific replied from the bot and based on the response 
you will output the user and consist the next post request to the same webhook


Get started
=============
This is the request body for the get started message

``Request``

the request contains the poatback type ``get_started`` make sure you identify our subscribers by a unique identifier in this format ``wb_`` + 16

.. code-block::

    curl --location --request POST 'https://messenger.botme.com/webhook' \
    --header 'Content-Type: application/json' \
    --data-raw '{
        "object": "web",
        "entry": [
            {
                "id": "wb_618819f454881e619a5f91b4",
                "time": 1636890098,
                "messaging": [
                    {
                        "recipient": {
                            "id": "<CID>"
                        },
                        "timestamp": 1636890098,
                        "sender": {
                            "id": "wb_BFzqMY5txPsbGTEw1LABDpM4W"
                        },
                        "postback": {
                            "payload": "{\"type\":\"get_started\",\"botId\":<BOT_ID>,\"packId\":\"<GETSTARTED_PACK_ID>\"}",
                            "title": "Get Started"
                        }
                    }
                ]
            }
        ],
        "preview": true
    }'

``Response``

the response is a message with two buttons like in the image below remember you will use each button payload 
to build the new payload to the same `webhook`_ request

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
                                    "payload": "{\"payload\":\"english60800f1a573a9\",\"botId\":<BOT_ID>,\"value\":\"English\",\"next_pack\":\"8d0f593b79be3c20acaaf388fd29845d\",\"button_type\":\"post_back\",\"button_id\":\"5f9ee977e7757f294855e063\"}"
                                },
                                {
                                    "title": "العربية",
                                    "type": "postback",
                                    "payload": "{\"payload\":\"\\u0627\\u0644\\u0639\\u0631\\u0628\\u064a\\u062960800f1a574cc\",\"botId\":<BOT_ID>,\"value\":\"\\u0627\\u0644\\u0639\\u0631\\u0628\\u064a\\u0629\",\"next_pack\":\"5d635f30f7bd33adb3f58456f1071530\",\"button_type\":\"post_back\",\"button_id\":\"5f9ee977e7757f294855e064\"}"
                                }
                            ]
                        }
                    }
                },
                "typing": 0
            }
        ]
    }


Payload explained
=============

you will deal alot with the payload for button/quick-reply so in this chapter 
we explain the payload in more details.

 ``payload`` : unique payload id for each button/quick-reply 
 

 ``botId`` : is the bot id mention in the bot configurations

 ``value`` : is the button/quick-reply text content 

 ``next_pack`` : the next pack id to be used in the next request if this button is clicked

 ``button_type`` : the available button types are ``post_back|quick_reply``

 ``button_id`` : is the button id to be used in the next request

.. code-block::

    {
        "payload": "english60800f1a573a9",
        "botId": "<BOT_ID>",
        "value": "<BUTTON TEXT CONTENT>",
        "next_pack": "<PACK_ID>",
        "button_type": "post_back",
        "button_id":"<BUTTON_ID>"
    }