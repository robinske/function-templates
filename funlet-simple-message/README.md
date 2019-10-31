# Simple Message Funlet

This Twilio Function is based on the [Twimlet of the same name][twimlet].

[twimlet]: https://www.twilio.com/labs/twimlets/message

It can be used as a drop-in replacement for the Twimlet, by using the URL
of the Twilio Function as a webhook with the same GET parameters.

Alternatively, it can be customized by setting properties in the
environment. GET and POST parameters are considered first, if provided,
then environment properties, then config properties declared in the script.

Environment properties are most convenient when you are using a single
instance of this script in your account. To customize multiple instances,
the recommended way is to modify the script parameters in the config object,
directly in the script.

## Stages

The Simple Message Funlet has a single stage:

| Stage | Addressing | Description |
| ----: | :--------- | :---------- |
|     1 | Caller     | Play one or several messages to the caller |

## Input

### Messages

A list of one or several text string messages,
each being a recording URL or a text to say.
*(Any string starting with 'http' is considered to be a URL)*

1. Event: a single `Message=` or a list of `Message[]=` parameters
2. Environment: up to five string messages,
  each in a separate environment property:
  - `FUNLET_MESSAGE1`,
  - `FUNLET_MESSAGE2`,
  - `FUNLET_MESSAGE3`,
  - `FUNLET_MESSAGE4`,
  - `FUNLET_MESSAGE5`
3. Script: `messages` config property with an array of string values

### Language

Text string, language code for text messages, e.g. 'en' or 'en-gb'.
Defaults to 'en': English with an American accent.

1. Event: `Language` parameter
2. Environment: `FUNLET_MESSAGE_LANGUAGE` environment property
3. Script: `language` config property

### Voice

Text string, voice for text messages, one of 'man', 'woman' or 'alice'.
Defaults to 'alice', who speaks in a large selection languages.

1. Event: `Voice` parameter
2. Environment: `FUNLET_MESSAGE_VOICE` environment property
3. Script: `voice` config property

## Output

This Twilio Function returns TwiML instructions for Twilio Voice.
