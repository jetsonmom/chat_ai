# chat_ai
###### api 주소 입력하기 드리고 질문을 입력하기.

!pip install openai
import os
import json
from openai import OpenAI

os.environ['OPENAI_API_KEY'] = ''

OpenAI.api_key = os.getenv("OPENAI_API_KEY")

client = OpenAI()

completion = client.chat.completions.create(
  model="gpt-4o-mini",
  messages=[
    {"role": "system", "content": "You are a helpful assistant."},
    {"role": "user", "content": "Hello!"}
  ]
)

print(completion.choices[0].message)
