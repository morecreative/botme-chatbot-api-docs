=========================
Persistent Menu
=========================
.. note::

    Make sure you put the correct values for `<BOT_ID>, <CID>, <SENDER_ID>, <GETSTARTED_PACK_ID> </requirements.html>`_

.. image:: _static/images/presistent_menu.*


You can use this request to fetch the persistent menu for the bot then use 
the `webhook`_ endpoint to build the request based on user selection from the menu

.. _webhook: /webhook.html
.. requirements: /requirements.html

Request
-------------

.. code-block::

    curl --location --request GET 'https://www.botme.com/web/menu?cid=<CID>' \
    --header 'Connection: keep-alive' \
    --header 'Accept: */*' \
    --header 'Referer: https://www.botme.com/dashboard/build/dashboard/<BOT_ID>/build-mode'

Response
-------------
The persistent menu in the image above would respond with this json

.. code-block::

    {
        "bot_id": <BOT_ID>,
        "created_at": "November 14th, 2021 at 14:32",
        "updated_at": "November 14th, 2021 at 14:34",
        "id": "61911df47acf6b194e7ccf34",
        "buttons": [
            {
                "id": "61911df47acf6b194e7ccf35",
                "type": "web_url",
                "url": "https://www.botme.com",
                "title": "Made By Botme"
            },
            {
                "id": "61911e6a062cb039d07edfc2",
                "next_pack": "979595e458e83f3a9dc9ba29d8b2ca83",
                "type": "postback",
                "payload": "{\"payload\":\"tickets list61911e6a0c88b\",\"botId\":\"<BOT_ID>\",\"value\":\"Tickets List\",\"next_pack\":\"979595e458e83f3a9dc9ba29d8b2ca83\",\"button_type\":\"post_back\"}",
                "title": "Tickets List"
            },
            {
                "id": "61911e7ac180e47faa074c56",
                "next_pack": "02a75f7d63dd39e8ba089edcab510016",
                "type": "postback",
                "payload": "{\"payload\":\"orders list61911e7ac2d73\",\"botId\":\"<BOT_ID>\",\"value\":\"Orders list\",\"next_pack\":\"02a75f7d63dd39e8ba089edcab510016\",\"button_type\":\"post_back\"}",
                "title": "Orders list"
            }
        ]
    }