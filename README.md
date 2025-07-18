# mcp-n8n-firecrawl

MCP Server and Client with n8n and Firecrawl
A comprehensive Model Context Protocol (MCP) implementation using n8n workflows, featuring an intelligent scraping agent client powered by Google Gemini and a robust server utilizing Firecrawl API for web content extraction.

🚀 Overview
This project demonstrates a complete MCP ecosystem built with n8n automation platform, showcasing the seamless integration between AI agents and web scraping capabilities. The implementation consists of two main components:

Scraping Agent Client: An intelligent conversational agent that can understand user requests and perform web scraping operations
MCP Server: A dedicated server that provides web scraping services through the Firecrawl API
🏗️ Architecture
The system follows a client-server architecture where the MCP client communicates with the MCP server through standardized protocols. The client leverages Google Gemini's language model capabilities to understand natural language requests and translate them into appropriate scraping operations.

Components
1. Scraping Agent Client (SCRAPINGAGENT.json)
Chat Trigger: Initiates conversations and receives user input
AI Agent: Core intelligence powered by Google Gemini
Memory Buffer: Maintains conversation context with a 15-message window
MCP Client Tool: Connects to the MCP server for scraping operations
2. MCP Server (MCPserverFirecrwal.json)
MCP Server Trigger: Handles incoming requests from clients
Scrape Tool: Performs web scraping using Firecrawl API with markdown output
🛠️ Prerequisites
Before setting up this project, ensure you have the following:

n8n instance (self-hosted or cloud)
Google Gemini API key
Firecrawl API key
ngrok account (for exposing local endpoints)
📦 Installation
1. Clone the Repository
git clone https://github.com/yourusername/mcp-n8n-firecrawl.git
cd mcp-n8n-firecrawl
2. Import n8n Workflows
Open your n8n instance
Navigate to Workflows → Import from File
Import SCRAPINGAGENT.json for the client workflow
Import MCPserverFirecrwal.json for the server workflow
3. Configure Credentials
Google Gemini API
Go to Credentials in your n8n instance
Create a new credential for "Google Gemini(PaLM) Api"
Enter your Google Gemini API key
Firecrawl API
Update the Authorization header in the scrape tool
Replace fc-1471844158c0428ea5980bea02469c8c with your Firecrawl API key
HTTP Header Authentication
Create credentials for "HTTP Header Auth"
Configure the header authentication for MCP server access
⚙️ Configuration
Server Setup
Activate the MCP Server Workflow

Open the MCP server Firecrwal workflow
Click Activate to start the server
Note the webhook URL generated
Configure ngrok (if using local n8n)

ngrok http 5678
Copy the generated ngrok URL
Update the MCP client endpoint in the scraping agent
Client Setup
Update MCP Client Configuration

Open the SCRAPING AGENT workflow
Navigate to the "MCP scrape Client" node
Update the sseEndpoint with your server URL
Format: https://your-domain.ngrok-free.app/mcp/da34892c-8018-4f03-9322-f49a2ed49853
Activate the Client Workflow

Click Activate to start the scraping agent
Note the chat webhook URL for testing
🚀 Usage
Starting a Conversation
Access the Chat Interface

Use the webhook URL from the chat trigger
Send POST requests with JSON payload:
{
  "message": "Please scrape the content from https://example.com"
}
Example Interactions

"Scrape the latest news from https://news.example.com"
"Extract the main content from this blog post: https://blog.example.com/post"
"Get the markdown content of this documentation page"
API Endpoints
Client Endpoint
POST https://your-domain.ngrok-free.app/webhook/91178f0e-a59d-4c0a-b006-f6d3a32d702d
Content-Type: application/json

{
  "message": "Your scraping request here"
}
Server Endpoint
POST https://your-domain.ngrok-free.app/mcp/da34892c-8018-4f03-9322-f49a2ed49853
🔧 Customization
Modifying Scraping Parameters
The Firecrawl scraping tool can be customized by modifying the JSON body in the scrape node:

{
  "url": "https://docs.firecrawl.dev",
  "formats": ["markdown"],
  "options": {
    "waitFor": 1000,
    "timeout": 30000
  }
}
Extending Memory
Adjust the context window length in the Simple Memory node:

Current setting: 15 messages
Recommended range: 10-50 messages depending on use case
Adding New Tools
To extend the agent's capabilities:

Create new tool nodes in the server workflow
Connect them to the MCP Server Trigger
Update the client to recognize new tool capabilities
🔍 Monitoring and Debugging
Workflow Execution Logs
Monitor execution logs in n8n for both workflows
Check for API rate limits and authentication issues
Verify webhook connectivity between client and server
Common Issues
Authentication Errors

Verify API keys are correctly configured
Check credential permissions and expiration
Connection Timeouts

Ensure ngrok tunnel is active
Verify firewall settings allow webhook traffic
Memory Issues

Monitor conversation context length
Clear memory buffer if responses become inconsistent
📊 Performance Considerations
Rate Limiting
Firecrawl API: Check your plan's rate limits
Google Gemini: Monitor token usage and requests per minute
Optimization Tips
Implement caching for frequently scraped URLs
Use batch processing for multiple URL requests
Configure appropriate timeout values
🔐 Security
Best Practices
Store API keys securely using n8n's credential system
Use HTTPS for all webhook communications
Implement rate limiting on client endpoints
Regularly rotate API keys
Access Control
Restrict webhook access using authentication headers
Monitor usage patterns for unusual activity
Implement logging for audit trails
🤝 Contributing
We welcome contributions to improve this MCP implementation:

Fork the repository
Create a feature branch
Make your changes
Submit a pull request
Development Guidelines
Follow n8n workflow best practices
Document any new nodes or configurations
Test thoroughly before submitting
📄 License
This project is licensed under the MIT License - see the LICENSE file for details.

🙏 Acknowledgments
n8n for the powerful automation platform
Firecrawl for reliable web scraping capabilities
Google Gemini for advanced language model integration
Model Context Protocol for standardized AI tool communication
📞 Support
For questions, issues, or contributions:

Create an issue in this repository
Contact: abhishek1530002@gmail.com
Documentation: Project Wiki
Built with ❤️ using n8n, Firecrawl, and Google Gemini
