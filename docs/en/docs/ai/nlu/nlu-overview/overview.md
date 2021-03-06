---
 title: "NLU Overview" 
 slug: "overview" 
 hidden: false 
---
# NLU Overview

**Natural Language Understanding** is at the core of advanced Virtual Agents. Cognigy.AI features an industry leading NLU engine called Cognigy NLU. 

## Intents
<div class="divider"></div>
Intent Mapping is at the core of the NLU engine and the process uses machine learning to match the user's utterance to the defined intents.

???+ info "Want to learn how to use Intents?"
    Head over to **[Train your Virtual Agent to recognize Intents](https://support.cognigy.com/hc/en-us/articles/360014776879-Train-your-Virtual-Agent-to-recognize-Intents)** in the Help Center.



<blockquote class="callout callout_info" theme="📘">
    <span class="callout-icon">▶️</span>
    <div class="callout-heading">
      <div class="callout-text">
         <a href="https://support.cognigy.com/hc/en-us/articles/360019857220-Cognigy-Sessions-Cognigy-NLU" target="_blank" >Techinar video "Cognigy NLU"</a>
      </div>
      <div class="callout-subtext">
      Watch this Episode of Cognigy Sessions for a technical deep dive
      </div>
   </div>
</blockquote>

**Intents** can be created right within the Intents section of the NLU tab and can be fed with **training data** in the form of **example sentences**. These example sentences should include a certain degree of variation for the model to work well. The following image shows an example intent library within the intent creation menu:

<figure>
  <img class="image-center" src="{{config.site_url}}ai/nlu/images/b3aad66-nlu-intents-trainingdata.jpg" width="100%" />
</figure>

Machine learning models work best with comparable amount of information on all intent classes. That is, ideally all intents have a similar amount of example sentence and are clearly separable in terms of content. While it is able to deal with imperfect input, it always helps if you make the job for the machine easier.

Make sure you do not have intents that are only a single word or sentence without useful information. Such intents may reduce the overall efficacy of the model.

### NLU model feedback

As soon as the model is trained, Cognigy NLU is able to provide feedback regarding the model's performance. This is shown using different colors, with green being good, orange being sub-optimal and red being bad. Additional information is given on mouse-hover.

???+ warning "Number of example sentences"
    Intents must have at least five example sentences in order to train the NLU.

### Rules
Rules can be used to trigger the Intent under specific conditions. Rules are defined as **JavaScript expressions** that are evaluated when the NLU is executed.

### Intent Entrypoint
Intent Entrypoints can be used to alter the Entrypoint in the Flow after the NLU is executed. The three options are:

  * **Execute normally**
   Automatically set the Entrypoint.

  * **Execute from START in this flow**
   Executes the Flow using the Start Node. 

  * **Execute from a Node in this flow** 
   Executes the flow starting from a specific Node.

<figure>
  <img class="image-center" src="{{config.site_url}}ai/nlu/images/53e2c9e-intents-entry.jpg" width="100%" />
</figure>

### Default Replies
Intents can be configured with direct output (answers) in the form of so-called **Default Replies**. Default Replies are integrated [**Say**]({{config.site_url}}ai/flow-nodes/message/say/) and can be configured with channel-specific output.

<figure>
  <img class="image-center" src="{{config.site_url}}ai/nlu/images/1d895b1-intents-default-reply.jpg" width="100%" />
</figure>

### Advanced 
Intents can be configured with a number of advanced options.

#### Tags
Tags can be used to categorize Intents, which makes it easier to manage them.

#### Condition
This field can contain a [CognigyScript ]({{config.site_url}}ai/tools/cognigy-script/) condition. The intent will only be found if the condition is true. Please wrap the entire condition in an "exists" operator:

```js
!!(ci.slots.city[0].keyphrase === "Düsseldorf")
```

or

```js
!!( !ci.text.includes("Cognigy"))
```

#### Confirmation Sentence
Cognigy NLU comes with an intent confirmation mechanism that works by configuring Confirmation Sentences in each intent. Whenever an Intent score falls within a (configurable) range - let's say 0,4 - 0,6, the Confirmation Sentence is triggered and shown to the user. If the user confirms the Intent, the Intent will be triggered.

???+ info "Adding Reconfirmation Sentences"
    Read more about how reconfirmation works on our [Machine Learning Intents]({{config.site_url}}ai/nlu/nlu-overview/ml-intents/) page.

### Intent Options Menu
The Intent Options Menu can be selected by clicking on the three dots next to the Create Intent button. The menu provides a number of options:

<figure>
  <img class="image-center" src="{{config.site_url}}ai/nlu/images/c83fb06-intents-menu.jpg" width="100%" />
</figure>

  * **Upload Intents CSV or JSON File**
This option lets you upload Intent collection in either CSV or JSON format. 

  * **Download Intents**
Intents can be downloaded in CSV and JSON formats as well.

  * **Create 'Reject Intent"**
Reject Intents can be used to explicitly filter out certain utterances. A Reject Intent can be used in case certain user utterances should not be registered as an Intent.

  * **Delete All Intents**
This option can be used to batch-delete all intents in a given Flow.

### Individual Intent Options Menu
Each intent additionally has its own options menu that can be selected by clicking on the three dots next to the Intent name. The menu provides a number of options:

  * **Create 'Child Intent"**
Adds an intent as a child intent to the selection. See [Intent Hierarchy]({{config.site_url}}ai/nlu/nlu-overview/intent-hierarchy/). This property is included on data import/export.

  * **Disable Intent**
Disables the selected intent so that it cannot be recognized or activated by a user input. This function temporarily removes the intent and it's associated training data from the model but allows for it to be re-added in a single click. This property is included on data import/export.

 * **Delete Intents**
Removes the intent and all associated training data from the model.

## Attachments
<div class="divider"></div>

Cognigy NLU can take into account additional Flows and Lexicons whenever they are attached.

### Attached Flows
Whenever a Flow with Intents is attached to another Flow, the Intents in that Attached Flow are taken into account when training the NLU model. This is a practical way of combining different Intent collections into a bigger model. 

???+ warning "Be careful with attaching Flows"
    Whenever a Flow is attached to another Flow, the Intents of both Flows are combined into a single model. This may lead to unexpected results.

### Attached Lexicons
Lexicons need to be attached to a Flow in order for a Flow to be able to detect its Keyphrases. Make sure to retrain the model whenever you attach or detach resources. 

## States
<div class="divider"></div>

States can be used to deliberately block certain Intents. This can help with edge-cases or very large Intent collection

???+ info "States"
    Refer to [**State**]({{config.site_url}}ai/tools/interaction-panel/state/) for more information.

## Slot Fillers
<div class="divider"></div>

<blockquote class="callout callout_info" theme="📘">
    <span class="callout-icon">▶️</span>
    <div class="callout-heading">
      <div class="callout-text">
         <a href="https://support.cognigy.com/hc/en-us/articles/360020609199-Cognigy-Sessions-Question-Nodes" target="_blank" >Techinar video "Question Nodes"</a>
      </div>
      <div class="callout-subtext">
      Watch this Episode of Cognigy Sessions for a technical deep dive
      </div>
   </div>
</blockquote>
    
Slot Fillers allow for advanced Slot filling with very little effort. They can be configured with a certain Type of Slot and are executed whenever the NLU is executed (typically with every input). Slot Fillers automatically copy found Slots to the [Context]({{config.site_url}}ai/tools/interaction-panel/context/)  object, meaning that they can be filled using a number of subsequent user utterances. When combined with Question Nodes, this allows for a very natural information gathering mechanism since it allows users to "over answer". 

**Example:**
Suppose we want to gather three pieces of information:

  * **Size**
  * **Email**
  * **Product**

We would configure appropriate **Slot Fillers** for these pieces of information:

<figure>
  <img class="image-center" src="{{config.site_url}}ai/nlu/images/f3a2f48-nlu-slot-filling.jpg" width="100%" />
</figure>

If we now add matching Question Nodes, we get following Flow:

<figure>
  <img class="image-center" src="{{config.site_url}}ai/nlu/images/8334ff0-nlu-slot-filling-flow.jpg" width="100%" />
</figure>

Make sure to configure the Question Nodes with the "Skip if Answer exists in Context" selected, as this is where the Slot Filler results are stored. 

<figure>
  <img class="image-center" src="{{config.site_url}}ai/nlu/images/3d699cb-nlu-slot-filling-question-node.jpg" width="100%" />
</figure>

The Flow is now ready to take different kinds of utterances and automatically ask for the missing information.

*"I would like a T-Shirt in XL"* -->**[missing email]**-->*"What is your email?"*.

*"I would like a T-Shirt in XL, and my email is max@cognigy.com"*--> **Flow completed.**


### Advanced Slot Filler Options

#### Additional Validation
A [CognigyScript]({{config.site_url}}ai/tools/cognigy-script/) condition which must return `true` in order for the match to be considered valid. An example would be an additional validation on an Email Question of `input.slots.EMAIL[0].endsWith("cognigy.com")` which would guarantee that only cognigy.com email addresses pass the validation.

#### Result Location
The location of a filled slot result is determined by default by the slot type (e.g., `input.slots.EMAIL[0]` for Email Questions). This can be overwritten using this setting (e.g., `input.slots.EMAIL` would store all found email slots). If the result location doesn't return a value (= is falsy), the answer will be considered invalid.