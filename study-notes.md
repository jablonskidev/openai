[**NOTE:** These study notes are **intentionally unstructured & rough**. I plan to jot down notes as I go along and put them in a more usable structure when I have a clearer idea of what problem I want this repo to solve for other people.]

---

**Table of contents:**
- [Tokens](#Tokens)
- [Parameters](#Parameters)
- [Models](#Models)
- [Prompt Engineering](#Prompt-Engineering)

---

## Tokens

- Tokens vs words: https://platform.openai.com/tokenizer
- Cost = input tokens + output tokens
- `max_tokens` to limit the number of tokens in output (default = 16)

## Parameters

- **`stop`:** https://platform.openai.com/docs/api-reference/completions/create#completions/create-stop
- **`n`:** https://platform.openai.com/docs/api-reference/completions/create#completions/create-n
- **`echo`:** https://platform.openai.com/docs/api-reference/completions/create#completions/create-echo

## Models

- Check out existing models: https://platform.openai.com/docs/models
- Use playground to compare results: https://platform.openai.com/playground

## Prompt Engineering

Here are components of an effective prompt:

| Component           | Example                                                                         |
|---------------------|---------------------------------------------------------------------------------|
| Task                | List the place names in the following text.                                     |
| Input data          | Text: "British Columbia borders Alberta, Yukon, and the Northwest Territories." |
| Output requirements | Desired format: <comma_separated_list>                                          |

You can use the completion model to:
- Summarize text
- Extract data
- Analyse sentiment
- Transform text (example: translating)

If you're not getting useful results, you can:
- Give examples of what you want (zero-shot vs one-shot vs few-shot prompting)
- Add "Let's think step by step" (chain of thought)
