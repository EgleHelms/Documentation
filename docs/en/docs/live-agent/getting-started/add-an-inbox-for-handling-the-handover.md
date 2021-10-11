# Add an Inbox for Handling The Handover

From the Live Agent **Dashboard** screen, doing click on **Inboxes** in the sidebar.

>You can also add new inboxes from the welcome message or clicking on the plus button next to Inboxes in the sidebar

Choose API as the inbox channel.

<img src="{{config.site_url}}assets/img/LA-add-inbox-screen.png" width="100%" alt="Live Agent Add Inbox screen">

Now for creating the inbox, a channel name and a webhook URL needs to be set. Go to the Cognigy endpoint editor for getting it.

<img src="{{config.site_url}}assets/img/LA-cognigy-endpoint-config-screen.png" width="100%" alt="Cognigy AI Endpoint config screen">

The webhook URL is the Cognigy.AI endpoint config URL domain plus `/handover/chatwoot`.

<img src="{{config.site_url}}assets/img/LA-add-api-channel-screen.png" width="100%" alt="Live Agent API channel screen">

<table>
<tr>
<th>Field</th>
<th>Example Value</th>
<th>Description</th>
</tr>
<tr>
<td>Channel Name</td>
<td>Live Agent Handover</td>
<td>Name for the channel name</td>
</tr>
<tr>
<td>Webhook URL</td>
<td>https://endpoint-trial.cognigy.com/handover/chatwoot</td>
<td>https://endpoint-trial.cognigy.com is the Cognigy.AI endpoint config URL domain</td>
</tr>
</table>

After that, agents need to be assigned to the new inbox. Start typing their names, pick them from the selector and click on **Add agents**.

<img src="{{config.site_url}}assets/img/LA-add-agents-to-inbox-screen.png" width="100%" alt="Live Agent API channel screen">

One more thing to do is note down the following data, the _Inbox ID_ and the _Account ID_. This can be found on the URL after creating the inbox.

<img src="{{config.site_url}}assets/img/LA-account-inbox-ids.png" width="100%" alt="Live Agent account ID and inbox ID">

<table>
<tr>
<th>Field</th>
<th>Example Value</th>
</tr>
<tr>
<td>Live Agent URL</td>
<td>cognigy-live-agent.com/app/accounts/1234/inbox/4405</td>
</tr>
<tr>
<td>Account ID</td>
<td>1234</td>
</tr>
</tr>
<tr>
<td>Inbox ID</td>
<td>4405</td>
</tr>
</table>

Now your inbox is ready to be used. You can now fill the _Account ID_ field in the **Endpoint Editor** plus the _API Key_ that can be found in Live Agent **Profile Settings** as per the screenshot.

<img src="{{config.site_url}}assets/img/LA-profile-settings-access-token.png" width="100%" alt="Live Agent Profile Settings API Key">

Now a handover flow needs to be connected to the inbox, head over to 
[Creating A Cognigy.AI Handover Flow](/live-agent/getting-started/creating-a-cognigy-handover-flow).