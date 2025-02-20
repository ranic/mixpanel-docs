---
title: "Server"
slug: "server"
hidden: false
createdAt: "2023-03-25T20:18:09.345Z"
updatedAt: "2023-03-26T23:48:54.396Z"
---
You can use Mixpanel's Server SDKs to send events from your backend servers to Mixpanel. We [recommend](doc:plan-your-implementation#need-to-start-tracking-product-data) server-side tracking, since it is more reliable and easier to maintain than web/mobile tracking.

### Step 1: Install the SDK
```shell Python
pip install mixpanel
```
```shell Node.js
npm install mixpanel
```
```shell Ruby
gem install mixpanel-ruby
```
```xml Java
<!--Include the following in your project's pom.xml-->
  <dependency>
    <groupId>com.mixpanel</groupId>
    <artifactId>mixpanel-java</artifactId>
    <version>1.4.4</version>
  </dependency>
```

### Step 2: Track your first event

You'll need your Project Token for this, which you can get [here](mixpanel.com/settings/project).
[block:code]
{
  "codes": [
    {
      "code": "from mixpanel import Mixpanel\nmp = Mixpanel(\"YOUR_TOKEN\")\n\n# Note: you must supply the user_id who performed the event as the first parameter.\nmp.track(user_id, 'Signed Up',  {\n  'Signup Type': 'Referral'\n})",
      "language": "python",
      "name": null
    },
    {
      "code": "var Mixpanel = require('mixpanel');\nvar mixpanel = Mixpanel.init('<YOUR_TOKEN>');\n\n// Note: you must supply the user_id who performed the event in the `distinct_id` field\nmixpanel.track('Signed Up', {\n  'distinct_id': user_id,\n  'Signup Type': 'Referral'\n})",
      "language": "javascript",
      "name": "Node.js"
    },
    {
      "code": "require 'mixpanel-ruby'\nmp = Mixpanel::Tracker.new(PROJECT_TOKEN)\n\n# Note: you must supply the user_id who performed the event as the first parameter\nmp.track(user_id, 'Signed Up', {\n\t'Signup Type' => 'Referral'\n})",
      "language": "ruby"
    },
    {
      "code": "import com.mixpanel.mixpanelapi.ClientDelivery;\nimport com.mixpanel.mixpanelapi.MessageBuilder;\nimport com.mixpanel.mixpanelapi.MixpanelAPI;\n\nMessageBuilder messageBuilder = new MessageBuilder(PROJECT_TOKEN);\n\n// You can send properties along with events\nJSONObject props = new JSONObject();\nprops.put(\"Signup Type\", \"Referral\");\n\n// Create an event\nJSONObject sentEvent = messageBuilder.event(userId, \"Signup\", props);\n\nClientDelivery delivery = new ClientDelivery();\ndelivery.addMessage(sentEvent);\n\n// Use an instance of MixpanelAPI to send the messages\n// to Mixpanel's servers.\nMixpanelAPI mixpanel = new MixpanelAPI();\nmixpanel.deliver(delivery);",
      "language": "java"
    }
  ]
}
[/block]
🎉 Congratulations, you've tracked your first event! You can see it in Mixpanel via the [Events](mixpanel.com/report/events) page. 

Don't see your language here? See all our libraries in [Github](https://www.github.com/mixpanel) and our references for [Python](doc:python), [Node](doc:nodejs), [Ruby](doc:ruby), and [Java](doc:java). We also have a simple [HTTP API](doc:cloud-ingestion) for any languages we don't support.
