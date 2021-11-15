=========================
Requirements
=========================

First you need these data to interact with the bot from your application, please contact 

``<BOT_ID>`` we use the bot id to identify which bot you are talking to.

``<CID>`` the channel id to identify the.

``<GETSTARTED_PACK_ID>`` the starter request simulate clicking on the ``Get Started`` button in the bot

``<YOUR_WEBSITE_DOMAIN>`` your website domain name needed in the refere of some request.

``<SENDER_ID>`` this should be random generated code for each person talking to the bot 

    .. warning::

        - Please follow this equation to generate unique random ``SENDER_ID``
        
            .. code-block::
            
                'wb_' + Math.random(50).toString(36).substr(2, 190);
        
        - Make sure that you need to save this random generated ``SENDER_ID`` per user.