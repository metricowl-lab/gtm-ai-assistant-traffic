# AI Assistant Traffic

A web variable template that tells you when a visit came from an AI assistant, such as ChatGPT, Perplexity, Gemini, Copilot or Claude. It returns the assistant's name, the label "AI assistant", or `true`/`false`, ready for a GA4 custom dimension or event parameter.

## Why

GA4's default channel group has an AI Assistant channel, but it only covers the assistants Google recognises and doesn't publish the full list. Other assistants show up as Referral. Some app visits arrive with no referrer at all, but ChatGPT adds `utm_source=chatgpt.com` to many of the links it cites. This variable checks both. Background: [How to track ChatGPT and other AI traffic in GA4](https://www.metricowl.co.uk/guides/track-ai-traffic-ga4).

## Set up

1. Add the template from the Community Template Gallery, or import `template.tpl` under **Templates**.
2. Create a variable from it, for example **AI Assistant**.
3. In your GA4 Google tag, add a configuration parameter such as `ai_assistant` with the value `{{AI Assistant}}`.
4. In GA4, register `ai_assistant` as an event-scoped custom dimension.

## Settings

| Setting | What it does |
|---|---|
| Return | The assistant's name (default), the label "AI assistant", or `true`/`false` |
| Value for other visits | Returned when it isn't an AI visit. Leave blank to return `undefined`, so GA4 doesn't send the parameter. |
| Also check utm_source | On by default. Uses `utm_source` when the referrer doesn't match. |
| Extra assistants | One per line as `hostname=Name`. Checked before the built-in list. |
| Referrer to check / Page address to check | Advanced: classify another value, such as a stored first-touch referrer |

## Built-in list

| Hostnames | Assistant |
|---|---|
| chatgpt.com, chat.openai.com | ChatGPT |
| perplexity.ai | Perplexity |
| gemini.google.com, bard.google.com | Gemini |
| copilot.microsoft.com, copilot.cloud.microsoft | Copilot |
| claude.ai | Claude |
| chat.deepseek.com | DeepSeek |
| chat.mistral.ai | Mistral |
| grok.com | Grok |
| meta.ai | Meta AI |
| you.com | You.com |
| poe.com | Poe |
| phind.com | Phind |

Subdomains match, such as `www.perplexity.ai`. Look-alikes such as `notchatgpt.com` don't, and nor do the companies' other sites, such as `help.openai.com` or `www.deepseek.com`. New assistants are added as they appear. Open an issue if one is missing.

## Permissions

Reads the page referrer and the page address.

## Licence

Apache License 2.0. See [LICENSE](LICENSE).

Built and maintained by Marc Alexander at [Metric Owl](https://www.metricowl.co.uk), a GA4 and Google Tag Manager consultancy in London. Issues and suggestions are welcome.
