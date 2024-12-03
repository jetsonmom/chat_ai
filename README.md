# chat_ai
###### api 주소 입력하기 드리고 질문을 입력하기.

![image](https://github.com/user-attachments/assets/0925f466-1c77-48bc-92eb-34cfa5277d5f)

```
!pip install openai
import os
import json
from openai import OpenAI

os.environ['OPENAI_API_KEY'] = 'xxxxxxxxxx'

OpenAI.api_key = os.getenv("OPENAI_API_KEY")

client = OpenAI()
def chat_with_gpt():
    print("GPT와 대화를 시작합니다. 종료하려면 'quit'를 입력하세요.")
    
    while True:
        # 사용자 입력 받기
        user_input = input("\n나: ")
        
        if user_input.lower() == 'quit':
            print("대화를 종료합니다.")
            break
        
        try:
            # GPT에 질문하기
            completion = client.chat.completions.create(
                model="gpt-4o-mini",
                messages=[
                    {"role": "system", "content": "You are a helpful assistant."},
                    {"role": "user", "content": user_input}
                ]
            )
            
            # 응답 출력
            response = completion.choices[0].message.content
            print(f"\nGPT: {response}")
            
        except Exception as e:
            print(f"오류 발생: {str(e)}")

if __name__ == "__main__":
    chat_with_gpt()
```
