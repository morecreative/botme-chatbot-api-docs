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


Button request
=============
from `Buton With Text </message_types.html#text-with-buttons>`_ section you can simulate the click on any button using this request
also you can replace ``BUTTON_PAYLOAD_VALUE`` and ``BUTTON_TITLE`` by the payload and button text user has selected.

.. code-block::

    curl --request POST \
    --url https://messenger.botme.com/webhook \
    --header 'Content-Type: application/json' \
    --header 'Referer: https://www.botme.com/' \
    --header 'User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/93.0.4577.63 Safari/537.36' \
    --header 'sec-ch-ua: "Google Chrome";v="93", " Not;A Brand";v="99", "Chromium";v="93"' \
    --header 'sec-ch-ua-mobile: ?0' \
    --header 'sec-ch-ua-platform: "Linux"' \
    --data '{
        "object": "web",
        "entry": [
            {
                "id": "<CID>",
                "time": 1551626486065,
                "messaging": [
                    {
                        "recipient": {
                            "id": "<CID>"
                        },
                        "timestamp": 1551626486065,
                        "sender": {
                            "id": "<SENDER_ID>"
                        },
                        "postback": {
                            "payload": "<BUTTON_PAYLOAD_VALUE>",
                            "title": "<BUTTON_TITLE>"
                        }
                    }
                ]
            }
        ],
        "preview": true
    }'

Quick reply request
=============
from `Buton with quick reply <//message_types.html#text-with-quick-replies>`_ section you can simulate the click on any quick reply using this request,
also you can replace ``QUICK_REPLY_PAYLOAD`` and ``QUICK_REPLY_TEXT`` by the payload and text user has selected.

.. code-block::

    curl --location --request POST 'https://messenger.botme.com/webhook' \
    --header 'Connection: keep-alive' \
    --header 'User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/93.0.4577.63 Safari/537.36' \
    --header 'Content-Type: application/json' \
    --header 'Accept: */*' \
    --header 'Origin: https://www.botme.com' \
    --header 'Referer: https://www.botme.com/' \
    --header 'Accept-Language: en-US,en;q=0.9' \
    --data-raw '{
        "object": "web",
        "entry": [
            {
                "id": "<CID>",
                "time": 1551626486065,
                "messaging": [
                    {
                        "recipient": {
                            "id": "<CID>"
                        },
                        "timestamp": 1551626486065,
                        "sender": {
                            "id": "<SENDER_ID>"
                        },
                        "postback": {
                            "payload": "<QUICK_REPLY_PAYLOAD>",
                            "title": "<QUICK_REPLY_TEXT>"
                        }
                    }
                ]
            }
        ],
        "preview": true
    }'

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