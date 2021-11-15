=========================
Webhook
=========================
.. note::

    Make sure you put the correct values for `<BOT_ID>, <CID>, <SENDER_ID>,<GETSTARTED_PACK_ID>  </requirements.html>`_


You can use the webhook to get specific replied from the bot and based on the response 
you will output the user and consist the next post request to the same webhook


Get started
=============
This is the request body for the get started message sending this request will simulate clicking on 
the ``Get Started`` Button in the conversation note you should send this request in the start of the conversation

``Request``

the request contains the poatback type ``get_started`` make sure you identify our subscribers by a unique identifier in this format ``wb_`` + 16

.. code-block::

    curl --location --request POST 'https://messenger.botme.com/webhook' \
    --header 'Content-Type: application/json' \
    --header 'Referer: https://www.botme.com/' \
    --data-raw '{
            "object": "web",
            "entry": [
                {
                    "id": "<CID>",
                    "time": 1636890098,
                    "messaging": [
                        {
                            "recipient": {
                                "id": "<CID>"
                            },
                            "timestamp": 1636890098,
                            "sender": {
                                "id": "<SENDER_ID>"
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
..

.. note::

    **Response can be different based on the conversation flow look at**  `Message Types </message_types.html>`_


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