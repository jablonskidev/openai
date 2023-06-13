[**NOTE:** These study notes are **intentionally unstructured & rough**. I plan to jot down notes as I go along and put them in a more usable structure when I have a clearer idea of what problem I want this repo to solve for other people.]

---

**Table of contents:**
- [Tokens](#Tokens)
- [Models](#Models)
- [Using the Completions API](#Using-the-Completions-API)
- [Using the Chat API](#Using-the-Chat-API)

---

## Tokens

- Tokens vs words: https://platform.openai.com/tokenizer
- Cost = input tokens + output tokens
- `max_tokens` to limit the number of tokens in output (default = 16)

## Models

- Check out existing models: https://platform.openai.com/docs/models
- Use playground to compare results: https://platform.openai.com/playground

## Using the Completions API

Here are some examples of what you can do with completions:
- Summarize text
- Extract data
- Analyse sentiment
- Transform text (example: translating)

Here are components of an **effective prompt**:

| Component           | Example                                                                         |
|---------------------|---------------------------------------------------------------------------------|
| Task                | List the place names in the following text.                                     |
| Input data          | Text: "British Columbia borders Alberta, Yukon, and the Northwest Territories." |
| Output requirements | Desired format: <comma_separated_list>                                          |

If you're not getting useful results, you can:
- Give examples of what you want (zero-shot vs one-shot vs few-shot prompting)
- Add "Let's think step by step" (chain of thought)

To control the **randonmness** of your output with the [completions API](https://platform.openai.com/docs/api-reference/completions), use the following parameters:

| Parameter   | Value  | Default | Under the Hood   |
|-------------|--------|---------|------------------|
| Temperature | 0 to 2 | 1       | Logits           |
| Top P       | 0 to 1 | 1       | Nucleus sampling |

To control the **repetitiveness** of your output with the [completions API](https://platform.openai.com/docs/api-reference/completions), use the following parameters:

| Parameter         | Value   | Default | Repetition        | Under the Hood                |
|-------------------|---------|---------|-------------------|-------------------------------|
| Frequency penalty | -2 to 2 | 0       | Individual tokens | Proportional contribution     |
| Presence penalty  | -2 to 2 | 0       | Topic             | One-off additive contribution | 

## Using the Chat API

You can use the chat API for:
- Back-and-forth conversation
- Single question and response

With the chat API, you can use:
- **`gpt-4`:** the most capable model
- **`gpt-3.5-turbo`:** the most cost-effective model

Here's an example of a request:
```
openai.ChatCompletion.create(
  model="gpt-3.5-turbo",
  messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": 'Translate the following English text to French: "I like trees."'},
        {"role": "assistant", "content": "J'aime les arbres."},
        {"role": "user", "content": 'Translate the following English text to French: "I collect moss."'},
        
    ]
)
```
You can use `role`, `user`, `assistant`, `system`, and `content` to give context and structure your request.

