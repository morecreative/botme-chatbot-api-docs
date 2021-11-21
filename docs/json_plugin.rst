=============
Json Plugin
=============
In This section you will learn more about botme json plugin how to structure your response and build your endpoint

.. image:: _static/images/json_composer.*


Build you endpoint 
===================
You can find the ``JSON API`` composer on the build mode, you can choose the type of the request if 
it is ``GET`` or ``POST`` and you have the fexibility to choose a token if you want you endpoint to be secured.

also you can click on ``Add Query Param +`` button so ask the user for input from the bot 
enter the 
    ``key`` which is the message that will appear to the bot user for example (What is you orderNo?)
    
    ``value`` is key that botme will use to attach the bot user response to that key and send it to your endpoint.

so imagine you endpoint is ``/webhook/bot`` and it is available under ``GET`` method 
so your endpoint should make one of the next responses so the bot can respond to your channel(messenger, whatsapp, webbot, etc)

Text message Response
=======================
Your endpoint response should be in this format 

.. code-block::

        {
            messaging_type: "RESPONSE",
            message: {
                text: "Hi There"
            }
        }

you can open Test the bot on the platform or start talking to your bot so you can get the response commng from your api.

    