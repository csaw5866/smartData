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

### One-Shot
We now tested a prompt where we give an example to the chatbot of what the final RDF should look like after the dataset was converted with the desired RML. It generated a great result at first try, not leaving much engineering to do: https://chat.openai.com/share/79530ca0-174a-49c5-8785-23d5cd3abeee . However, there were were a few particularities separating this from the previous attempts. Most notably, the created RML did specify a template for what the data should look like for some of the properties. This is likely due to the fact that the chatbot only had access to a singular example, which led it to believe every other example is structured alike. Doing this is a double-edged sword. On one hand, more specifity can be helpful for checking data correctness. On the other hand, it can also lead to examples classified wrongly because too much specificity was asked, and some data doesn't adhere to this structure. For this dataset, it works with this specificity, but it wouldn't for many other.

### Few-Shot
Next up was few-shot prompting. In contrast to the methods of prompt engineering tested above, we here provide the bot with multiple examples of our desired output in order to tune it to generate the best possible output. The initial prompt here was similar to the one-shot, generate a RML based on a given output RDF, but this time with multiple examples: https://chat.openai.com/share/00684ee0-d060-4124-b1c3-d2d5fe6876be . This came with a few surprises. First, this few-shot didn't generate the specific semantic requirements enforced by the RML from the one-shot. This is especially surprising because now there are multiple examples adhering to the same structure. Next, it automatically added the statements to add the data to the corresponding schema.org classes and properties. Whereas this was not observed for the zero-shot prompting, this likely comes from the provided RDF, as the example given was mapped ont schema.org.


### Comparison
First, let's compare the directly generated RDF to the best generated RML Mapping. First of all, the RML generation has the advantage that it generates a template that can be used on a large amount of instances. Contrary, when directly generating a RDF, there is an imposed limitation as a chatbot only accepts a certain amount of characters. Next, with the generated RML mappings from above, the instances are automatically classified into the corresponding schema.org onthologies, whereas the directly generated RDF did not do that. This however is a slightly unfair comparison, as we asked the model specifically in the RML case to map the instances onto schema.org, wheras we did not for the RDF generation. 


Next, let's compare the different prompting methods. Whereas all the methods produced comparable end results, the major difference observable here is the amount of manual interventions required in order for the chatbot to provide us with the wanted result. For zero-shot, we needed to specify both the shape of our data, as well as the fact that it should map onto schema. For one shot, this was not necessary, however, some wrong assumptions were taken from the data, which needed to be corrected, as well as the fact that the RML file should not include a concrete example. The few-shot did not require any of these rectifications. 
