# Prompting

This folder will contain all the prompt engineering we did on the IMDB Dataset. Most of it will porbably be provided in form of links to the respective conversations with ChatGPT 3.5.

In a first step, tried Zero-Shot and One-Shot prompting on the Dataset using ChatGPT 3.5, as well as some small error correction. The result is promising and seems to work just fine: https://chat.openai.com/share/86e5604b-a785-4b35-9cc0-0d464dc21e33 .
However, this was not what we were tasked to do. Hence, we engineered the following prompting attempts.

### Zero-Shot
Next, we prompted the LLM to create a RML file for us. The only information it was given was the structure of our data (as a singular film example), and the fact that it should already map everything to the corresponding schema.org onthologies. The result with only this information was very promising:
https://chat.openai.com/share/9b65bf58-d3fd-4b27-becd-63b001be8292