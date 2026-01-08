# Claude AI Integration

This document provides detailed information about using Claude AI with Termux AI.

## Overview

[Claude](https://www.anthropic.com/claude) is Anthropic's family of AI language models designed to be helpful, harmless, and honest. In Termux AI, Claude serves as one of the primary AI providers for command assistance, code generation, and intelligent terminal interactions.

## Why Claude?

### Key Advantages
- **Long Context Window** - Handle extensive command histories and project contexts
- **Technical Proficiency** - Excellent at understanding shell commands and programming
- **Safety & Reliability** - Constitutional AI principles ensure consistent, safe responses
- **Code Generation** - Strong capabilities in script and code generation
- **Clear Explanations** - Provides detailed, easy-to-understand command explanations

### Best Use Cases
- Complex shell scripting and automation
- Debugging command errors
- Project-aware development assistance
- Learning new terminal commands and workflows
- Multi-step command sequences

## Getting Started

### 1. Obtain API Key

1. Visit [console.anthropic.com](https://console.anthropic.com/)
2. Sign up or log in to your account
3. Navigate to **API Keys** section
4. Click **Create Key**
5. Copy your API key (it starts with `sk-ant-`)

### 2. Configure in Termux AI

1. Open Termux AI app
2. Go to **Settings** → **AI Integration**
3. Select **Claude** as your AI provider
4. Paste your API key in the **API Key** field
5. Choose your preferred model (see [Available Models](#available-models))
6. Save settings

### 3. Verify Connection

Run a test command or ask Claude for help:
```bash
# Type any command and wait for AI suggestions
ls -la

# Or use the AI assistance panel
# (Access via floating button or gesture)
```

## Available Models

### Claude 3.5 Sonnet (Recommended)
- **Model ID**: `claude-3-5-sonnet-20241022`
- **Best for**: Balanced performance and cost
- **Context**: 200K tokens
- **Use when**: General terminal assistance and development

### Claude 3 Opus
- **Model ID**: `claude-3-opus-20240229`
- **Best for**: Most complex tasks requiring deep reasoning
- **Context**: 200K tokens
- **Use when**: Complex debugging, architecture decisions

### Claude 3 Haiku
- **Model ID**: `claude-3-haiku-20240307`
- **Best for**: Fast, lightweight responses
- **Context**: 200K tokens
- **Use when**: Quick command suggestions, simple queries

### Claude 3.5 Haiku
- **Model ID**: `claude-3-5-haiku-20241022`
- **Best for**: Fastest responses with improved capabilities
- **Context**: 200K tokens
- **Use when**: Real-time command assistance

## Features

### Command Assistance
Claude analyzes your commands in real-time and provides:
- **Syntax validation** - Catch errors before execution
- **Alternative suggestions** - Better ways to accomplish tasks
- **Flag explanations** - What each option does
- **Safety warnings** - Alerts for potentially destructive commands

### Error Analysis
When commands fail, Claude:
- Analyzes error messages
- Explains what went wrong
- Suggests fixes
- Provides working alternatives

### Natural Language Commands
Convert English to shell commands:
```
You: "find all python files modified in the last week"
Claude: find . -name "*.py" -mtime -7
```

### Context-Aware Help
Claude understands your:
- Current directory and project type
- Recent command history
- Installed packages and tools
- Environment variables

### Code Generation
Generate scripts and code:
- Bash/shell scripts
- Python automation
- Text processing (awk, sed)
- Git workflows
- Build scripts

## API Configuration

### Environment Variables
You can also set your API key via environment variable:
```bash
export ANTHROPIC_API_KEY="sk-ant-..."
```

### Rate Limits
- **Free Tier**: Limited requests per month
- **Paid Tier**: Higher rate limits based on usage tier
- See [Anthropic Pricing](https://www.anthropic.com/pricing) for details

### Request Timeout
Default timeout: 30 seconds. Adjust in settings if needed.

## Best Practices

### Optimize Token Usage
- Keep command histories concise
- Clear AI context periodically
- Use Haiku for simple queries
- Reserve Opus for complex tasks

### Privacy & Security
- Never share commands containing passwords or API keys
- Use command filtering in Privacy Settings
- API keys are stored encrypted locally
- Sensitive patterns are filtered by default

### Performance Tips
- Enable caching for faster responses
- Use background processing for complex queries
- Adjust suggestion frequency based on usage patterns

## Troubleshooting

### "Invalid API Key" Error
- Verify key starts with `sk-ant-`
- Check for extra spaces or characters
- Ensure key is still active in Anthropic Console
- Try regenerating the key

### "Rate Limit Exceeded"
- Wait before retrying (typically 1 minute)
- Check your usage in Anthropic Console
- Consider upgrading your plan
- Use Haiku for lighter queries

### Slow Responses
- Check internet connection
- Try Haiku model for faster responses
- Reduce context window size in settings
- Clear cached contexts

### No Suggestions Appearing
- Verify AI provider is set to Claude
- Check API key is configured
- Ensure suggestions are enabled in settings
- Restart the app

### Connection Errors
- Verify internet connectivity
- Check if Anthropic API is operational ([status.anthropic.com](https://status.anthropic.com))
- Try increasing request timeout
- Check for network restrictions/firewalls

## Advanced Usage

### Custom System Prompts
Configure Claude's behavior in Advanced Settings:
- Set default context preferences
- Define custom command filters
- Adjust verbosity levels

### Project-Specific Configuration
Create `.termux-ai/claude.config` in your project:
```json
{
  "model": "claude-3-5-sonnet-20241022",
  "temperature": 0.7,
  "max_tokens": 1024,
  "context_files": [".gitignore", "README.md"]
}
```

### Keyboard Shortcuts
- `Ctrl+Space` - Trigger AI suggestion
- `Ctrl+Shift+A` - Open AI panel
- `Ctrl+Shift+E` - Explain last error

## API Reference

### Endpoint Used
```
POST https://api.anthropic.com/v1/messages
```

### Request Format
```json
{
  "model": "claude-3-5-sonnet-20241022",
  "max_tokens": 1024,
  "messages": [
    {
      "role": "user",
      "content": "Command or query here"
    }
  ],
  "system": "You are a helpful terminal assistant..."
}
```

## Resources

- **Anthropic Documentation**: [docs.anthropic.com](https://docs.anthropic.com/)
- **API Reference**: [docs.anthropic.com/api](https://docs.anthropic.com/api)
- **Model Comparison**: [anthropic.com/claude](https://www.anthropic.com/claude)
- **Pricing**: [anthropic.com/pricing](https://www.anthropic.com/pricing)
- **Status Page**: [status.anthropic.com](https://status.anthropic.com)

## Support

### Termux AI Specific Issues
- [GitHub Issues](https://github.com/your-username/termux-ai/issues)
- Tag issues with `claude` label

### Claude API Issues
- [Anthropic Support](https://support.anthropic.com)
- [Community Forum](https://community.anthropic.com)

## Comparison with Gemini

| Feature | Claude | Gemini |
|---------|---------|---------|
| Context Window | 200K tokens | 1M+ tokens (Gemini 1.5) |
| Code Generation | Excellent | Very Good |
| Command Understanding | Excellent | Very Good |
| Response Speed | Fast | Very Fast |
| Cost | Moderate | Lower (free tier generous) |
| Best For | Complex reasoning, safety-critical | Large contexts, multimodal |

## Privacy Statement

When using Claude:
- Commands are sent to Anthropic's API for processing
- Data is encrypted in transit (TLS)
- Anthropic's data usage policy applies
- See [Anthropic Privacy Policy](https://www.anthropic.com/privacy)
- Local filtering prevents sensitive data transmission

## Future Enhancements

Planned Claude-specific features:
- [ ] Claude Vision integration for image analysis
- [ ] Extended Thinking mode for complex problems
- [ ] Prompt caching for faster repeated queries
- [ ] Multi-turn conversations with memory
- [ ] Custom model fine-tuning support

---

**Last Updated**: January 2026
**Termux AI Version**: Compatible with v1.0+
**Claude API Version**: 2023-06-01
