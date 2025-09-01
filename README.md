# WhatsApp AI Chatbot with Node-RED

A sophisticated Node-RED flow that creates an intelligent WhatsApp chatbot powered by Meta's Llama AI model through the OpenRouter API. This solution provides secure, filtered AI-powered responses to WhatsApp messages with built-in phone number authentication.

## 🚀 Features

- **AI-Powered Conversations**: Utilizes Meta Llama 3.3 8B Instruct model for intelligent responses
- **WhatsApp Integration**: Seamlessly processes incoming WhatsApp messages
- **Security First**: Phone number whitelist filtering with E.164 normalization
- **Message Processing**: Handles multiple WhatsApp message formats (text, media captions, etc.)
- **Configurable AI**: Customizable system prompts and temperature settings
- **Production Ready**: Error handling and message validation

## 📋 Prerequisites

- Node-RED installation
- OpenRouter API account and key
- WhatsApp Business API or compatible WhatsApp integration
- Valid phone numbers in E.164 format for whitelist

## 🛠 Installation

1. **Import the Flow**
   - Copy the contents of `flows.json`
   - In Node-RED, go to Menu → Import → Clipboard
   - Paste the JSON and deploy

2. **Configure Your Settings**
   - Update the `allowedNumbers` array with your authorized phone numbers
   - Replace the OpenRouter API key with your own
   - Modify the AI system prompt if needed

## ⚙️ Configuration

### Phone Number Whitelist
```javascript
const allowedNumbers = [
  "+911234567890",  // Replace with your numbers
  "+1234567890"     // Add more as needed
];
```

### OpenRouter API Settings
```javascript
msg.headers = {
  Authorization: "Bearer YOUR_API_KEY_HERE",
  "Content-Type": "application/json",
  "X-Title": "Node-RED WhatsApp Bot"
};
```

### AI Model Configuration
```javascript
msg.payload = {
  model: "meta-llama/llama-3.3-8b-instruct:free",
  temperature: 0.7,
  // Add other parameters as needed
};
```

## 🔧 How It Works

1. **Message Reception**: Receives WhatsApp messages through Node-RED
2. **Phone Validation**: Normalizes phone numbers and checks against whitelist
3. **Message Processing**: Extracts text content from various WhatsApp message formats
4. **AI Processing**: Sends processed message to OpenRouter API with Llama model
5. **Response Delivery**: Returns AI-generated response back to WhatsApp

## 📱 Message Format Support

The flow handles multiple WhatsApp message types:
- Plain text messages
- Media with captions
- Message objects with nested content
- Various WhatsApp API formats

## 🔒 Security Features

- **Phone Number Filtering**: Only authorized numbers can interact with the bot
- **E.164 Normalization**: Ensures consistent phone number format
- **Input Validation**: Validates message structure and content
- **Error Handling**: Graceful handling of malformed messages

## 🎯 AI Behavior

The chatbot is configured to:
- Keep responses concise and under 800 characters
- Maintain friendly, helpful tone
- Avoid markdown formatting unless requested
- Handle images and links with plain text responses

## 🚀 Getting Started

1. **Test the Flow**
   - Deploy the flow in Node-RED
   - Send a test message from an authorized number
   - Verify the AI response is received

2. **Customize Responses**
   - Modify the system prompt in the function node
   - Adjust temperature for response creativity
   - Add custom message handling logic

## 📝 Customization Options

### System Prompt
Modify the AI's behavior by updating the system message:
```javascript
{ 
  role: "system", 
  content: "Your custom system prompt here..." 
}
```

### Response Limits
Adjust character limits and formatting preferences in the system prompt.

### Additional Features
- Add conversation history management
- Implement user-specific settings
- Include media handling capabilities
- Add webhook integrations

## 🔧 Troubleshooting

### Common Issues

1. **Messages Not Processing**
   - Check phone number format (must be E.164)
   - Verify number is in whitelist
   - Confirm OpenRouter API key is valid

2. **API Errors**
   - Validate OpenRouter API credentials
   - Check rate limits and usage
   - Verify model availability

3. **WhatsApp Integration**
   - Ensure proper webhook configuration
   - Check message format compatibility
   - Verify Node-RED connectivity

## 📊 Performance Considerations

- **Rate Limiting**: Monitor OpenRouter API usage
- **Message Volume**: Consider implementing queuing for high traffic
- **Error Handling**: Implement retry logic for failed requests
- **Logging**: Add comprehensive logging for debugging

## 🤝 Contributing

Contributions are welcome! Please feel free to:
- Report bugs and issues
- Suggest new features
- Submit pull requests
- Improve documentation

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🙏 Acknowledgments

- OpenRouter for AI API services
- Meta for the Llama AI model
- Node-RED community for the excellent platform
- WhatsApp Business API for messaging capabilities

## 📞 Support

For questions, issues, or contributions:
- Create an issue in this repository
- Check Node-RED community forums
- Review OpenRouter documentation

---

**Note**: This is a basic implementation intended for learning and small-scale use. For production deployments, consider additional security measures, error handling, and scalability improvements.