# Research Seminar Smart Data of Saqib Razzaq and Joey Hieronimy

This repository contains all the resources, code and documentation of Task 3 from the Research Seminar: Smart Data Group 4 of Saqib Razzaq and Joey Hieronimy.

First try of generating a RML Mapping in a certain style using ChatGPT, some sample data, and zero-shot- as well as one-shot prompting:
https://chat.openai.com/share/26ed6529-dd2b-48ce-8499-5d011b242fe7

In a first step, tried Zero-Shot and One-Shot prompting on the Dataset using ChatGPT 3.5, as well as some small error correction. The result is promising and seems to work just fine: https://chat.openai.com/share/86e5604b-a785-4b35-9cc0-0d464dc21e33 .
However, this was not what we were tasked to do. Hence, we engineered the following prompting attempts.

### Zero-Shot
Next, we prompted the LLM to create a RML file for us. The only information it was given was the structure of our data (as a singular film example), and the fact that it should already map everything to the corresponding schema.org onthologies. The result with only this information was very promising:
https://chat.openai.com/share/9b65bf58-d3fd-4b27-becd-63b001be8292

Next, we thought that the chatbot had a bit too much information to work with. This is why in the next attempt, we completely left out any information related to the specifics of our data. We only prompted the bot to generate us a RML for a film dataset. Altough the result wasn't great, it did manage to do some things right. Afterwards, we fed it more and more specifics, like the column names, and later that it should map to schema.org, which then resulted in a great output, nearly identical to the above: https://chat.openai.com/share/2880e2b6-3ab2-4900-8863-e26a8337fd5e

The last zero-shot attempt was to make the bot generate a RML file based on a singular example of the data rather than providing it the columns. This led to an interesting output, because at first, it refused to generate the entire file, and after telling it to do so, a RML file much different from the ones above was created. Rather than only mapping the data in CSV format on which the RML file would later be applied, this RML file automatically already maps the data for the film from the prompt: https://chat.openai.com/share/f97d8d20-b609-4dba-87a4-911a4bfe38b1
