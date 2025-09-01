# WhatsApp AI Chatbot for Node-RED

A tired developer’s shortcut: use this Node-RED flow to get a WhatsApp bot that actually replies with AI and ignores random numbers.

## Features

- **E.164 phone whitelist** so you don’t get spammed.
- Extracts text from most WhatsApp message shapes.
- Pipes everything to Meta’s Llama 3 via OpenRouter, gets a reply.
- Droppable function node for all configuration: allowed numbers, API key, system prompt.
- Debug node included to see what’s breaking (it will, sometimes).

## Quick Setup

1. Import `flows.json` into Node-RED.
2. Edit the function node:  
   Replace `allowedNumbers` with your phone numbers.
3. Swap the API key with yours (don’t use the sample key!).
4. Deploy and WhatsApp your bot from an allowed number.

---

## Visual Flow



![Node-RED WhatsApp Flow](assets/image.jpg)

---

## How It Works (explain like I’m five)

- Message comes from WhatsApp → Node-RED gets it
- If your number matches the allowed list, it sends your text to the AI
- Gets a reply and sends it back on WhatsApp
- If not, it ignores you.  
- Check the debug node when things go wrong

## Security Tip

Don’t commit your real API key.  
Don’t accept messages from everyone, unless you’re bored.

## License

MIT. Do what you want, but don’t blame me if it breaks.

---

Happy automating!
