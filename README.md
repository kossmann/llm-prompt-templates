# 🤖 LLM Prompt Templates

This is my personal repository of Prompt Templates for Large Language Models (LLMs) that I use daily.

I primarily use these templates with [Simon Willison's `llm` CLI utility](https://github.com/simonw/llm). If you're curious about how to get started with it, I wrote a detailed guide on my blog: [Quick Guide to Using the `llm` CLI Utility](https://www.danielkossmann.com/quick-guide-using-llm-cli-utility-python-library-simon-willison/).

I plan to keep this repository up to date with new templates as I create them.

My hope is that sharing this collection will inspire others to build and share their own prompt templates for LLMs.

Feel free to explore, adapt, and contribute!

## Templates

### improve-english.yaml

This template helps me write messages and learn from my mistakes, as I'm not a native English speaker. It provides corrections and suggestions to improve my English writing skills.

🧠 Optimized for: `openai/gpt-4.1-mini`

#### Input
Text content to be improved.

Example:
```
In the sidebar, you can click on Customize sidebar for additional settings. One that I found usefull was Move sidebar to the right, so I don't get distracted by the tabs while I'm browsing. I tried using Expand sidebar on hover but this is not very responsive (like all softwares that tries to do this).

```

#### Output
JSON with the following structure:
```json
{
  "original_sentence": "string",
  "error_analysis": [
    {
      "mistake": "string",
      "correction": "string",
      "explanation": "string",
    },
  ],
  "corrected_versions": {
    "concise_natural": "string",
    "friendly_engaging": "string",
    "smooth_polished": "string",
  }
}
```

Example:
```json
{
  "original_sentence": "In the sidebar, you can click on Customize sidebar for additional settings. One that I found usefull was Move sidebar to the right, so I don't get distracted by the tabs while I'm browsing. I tried using Expand sidebar on hover but this is not very responsive (like all softwares that tries to do this).",
  "error_analysis": [
    {
      "mistake": "Spelling mistake: 'usefull'",
      "correction": "useful",
      "explanation": "The correct spelling is 'useful' with a single 'l'."
    },
    {
      "mistake": "Capitalization inconsistency: 'Move sidebar to the right', 'Expand sidebar on hover'",
      "correction": "'Move sidebar to the right', 'Expand sidebar on hover' (use lowercase unless these are exact button labels)",
      "explanation": "If these are not exact button or menu item names, they should be lowercase. Otherwise, quote or clarify."
    },
    {
      "mistake": "Article usage and sentence clarity in 'One that I found useful was Move sidebar to the right'",
      "correction": "One setting I found useful was moving the sidebar to the right",
      "explanation": "'One that I found useful' is unclear. Use 'One setting' and the gerund 'moving' for clarity."
    },
    {
      "mistake": "Incorrect plural and verb agreement: 'softwares that tries'",
      "correction": "software that tries",
      "explanation": "'Software' is an uncountable noun and should not be pluralized. Also, 'software that tries' uses the correct singular verb."
    },
    {
      "mistake": "Awkward phrasing: 'this is not very responsive (like all softwares that tries to do this)'",
      "correction": "this isn’t very responsive, like most software that tries to do this",
      "explanation": "More natural phrasing improves fluidity and correctness."
    }
  ],
  "corrected_versions": {
    "concise_natural": "In the sidebar, you can click on Customize sidebar for more settings. One I found useful was moving the sidebar to the right, so I don't get distracted by tabs while browsing. I tried using Expand sidebar on hover, but it’s not very responsive, like most software that tries to do this.",
    "friendly_engaging": "Hey, in the sidebar, you can click Customize sidebar for extra settings. I really like moving the sidebar to the right—it keeps me from getting distracted by tabs when I’m browsing. I also tried the Expand sidebar on hover, but it’s kinda slow to respond, like most software that does this.",
    "smooth_polished": "In the sidebar, you can click on Customize sidebar to access additional settings. One feature I found particularly helpful is moving the sidebar to the right, which helps me avoid distractions from the tabs while browsing. I also tried the Expand sidebar on hover option, but it isn’t very responsive, similar to most software with this feature."
  }
}
```