# Vongenial-journey
Create function complex language {{Enable:API:Key}}
Enable:API:Key Python
"""
At the command line, only need to run once to install the package via pip:
$ pip install google-generativeai
"""

import google.generativeai as genai

genai.configure(api_key="YOUR API KEY")

defaults = {
  'model': 'models/text-bison-001',
  'temperature': 0.1,
  'candidate_count': 1,
  'top_k': 40,
  'top_p': 0.95,
  'max_output_tokens': 1024,
}
prompt = """Who are all the people and places named in the paragraph below? Respond in JSON.

Paragraph: ﻿Apollo 11 launched from Cape Kennedy on July 16, 1969, carrying Commander Neil Armstrong, Command Module Pilot Michael Collins and Lunar Module Pilot Edwin "Buzz" Aldrin into an initial Earth-orbit of 114 by 116 miles. An estimated 650 million people watched Armstrong's televised image and heard his voice describe the event as he took "...one small step for a man, one giant leap for mankind" on July 20, 1969. ﻿"""

response = genai.generate_text(
  **defaults,
  prompt=prompt
)
print(response.result)
Please Read if not the listed above then Javascript 
const { TextServiceClient } = require("@google-ai/generativelanguage");
const { GoogleAuth } = require("google-auth-library");

const MODEL_NAME = "models/text-bison-001";
const API_KEY = "YOUR API KEY";

const client = new TextServiceClient({
  authClient: new GoogleAuth().fromAPIKey(API_KEY),
});

const promptString = "Who are all the people and places named in the paragraph below? Respond in JSON.\n\nParagraph: ﻿Apollo 11 launched from Cape Kennedy on July 16, 1969, carrying Commander Neil Armstrong, Command Module Pilot Michael Collins and Lunar Module Pilot Edwin \"Buzz\" Aldrin into an initial Earth-orbit of 114 by 116 miles. An estimated 650 million people watched Armstrong's televised image and heard his voice describe the event as he took \"...one small step for a man, one giant leap for mankind\" on July 20, 1969. ﻿";

client.generateText({
  // required, which model to use to generate the result
  model: MODEL_NAME,
  // optional, 0.0 always uses the highest-probability result
  temperature: 0.1,
  // optional, how many candidate results to generate
  candidateCount: 1,
  // optional, number of most probable tokens to consider for generation
  top_k: 40,
  // optional, for nucleus sampling decoding strategy
  top_p: 0.95,
  // optional, maximum number of output tokens to generate
  max_output_tokens: 1024,
  prompt: {
    text: promptString,
  },
}).then(result => {
  console.log(JSON.stringify(result, null, 2));
});
