# What are OpenAPI/Request Tokens?
Tokens can be thought of as pieces of words. Before the API processes the request, the input is broken down into tokens. These tokens are not cut up exactly where the words start or end - tokens can include trailing spaces and even sub-words. Here are some helpful rules of thumb for understanding tokens in terms of lengths:

1 token ~= 4 chars in English

1 token ~= ¾ words

100 tokens ~= 75 words

Or 

1-2 sentence ~= 30 tokens

1 paragraph ~= 100 tokens

1,500 words ~= 2048 tokens

# Token Limits
Depending on the model used, requests can use up to 128,000 tokens shared between prompt and completion. Some models, like GPT-4 Turbo, have different limits on input and output tokens.
There are often creative ways to solve problems within the limit, e.g. condensing your prompt, breaking the text into smaller pieces, etc.

Exploring tokens
The API treats words according to their context in the corpus data. Models take the prompt, convert the input into a list of tokens, processes the prompt, and convert the predicted tokens back to the words we see in the response.

What might appear as two identical words to us may be generated into different tokens depending on how they are structured within the text. Consider how the API generates token values for the word ‘red’ based on its context within the text:
![![image](https://github.com/InaArya/AIML_Notes/assets/95537907/ce6e144a-a5fc-4cb2-a31d-1b9b71ac128f)
]
![![image](https://github.com/InaArya/AIML_Notes/assets/95537907/153a2853-7965-44ce-b4f3-ca70971e3f8e)
]
In the first example above the token “2266” for ‘ red’ includes a trailing space (Note, these are example token ID's for demonstration purposes).

![![image](https://github.com/InaArya/AIML_Notes/assets/95537907/bc6096b9-8ae9-4064-8d24-cb2948988f78)
]
![![image](https://github.com/InaArya/AIML_Notes/assets/95537907/c5170282-e82c-4fbf-9af6-e81f35a997cd)
]
The token “2296” for ‘ Red’ (with a leading space and starting with a capital letter) is different from the token “2266” for ‘ red’ with a lowercase letter.

The token “2296” for ‘ Red’ (with a leading space and starting with a capital letter) is different from the token “2266” for ‘ red’ with a lowercase letter.]

To further explore tokenization, you can use our interactive Tokenizer tool, which allows you to calculate the number of tokens and see how text is broken into tokens

# Observations:
The more probable/frequent a token is, the lower the token number assigned to it:
The token generated for the period is the same (“13”) in all 3 sentences. This is because, contextually, the period is used pretty similarly throughout the corpus data.
The token generated for ‘red’ varies depending on its placement within the sentence:
Lowercase in the middle of a sentence: ‘ red’ - (token: “2266”)
Uppercase in the middle of a sentence: ‘ Red’ -  (token: “2297”)
Uppercase at the beginning of a sentence: ‘Red’ - (token: “7738”)
