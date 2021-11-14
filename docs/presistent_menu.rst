=========================
Presistent Menu
=========================
you can use this request to fetch the presistent menu for the bot then use 
the `webhook`_ endpoint to consist request based on user selection from the menu

.. _webhook: /webhook.html

Make sure you put the corect values for <BOT_ID> and <CID>
.. code-block::

    curl --location --request GET 'https://www.botme.com/web/menu?cid=<CID>' \
    --header 'Connection: keep-alive' \
    --header 'Accept: */*' \
    --header 'Referer: https://www.botme.com/dashboard/build/dashboard/<BOT_ID>/build-mode'