import requests

API_KEY = "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"

def chat(message):
    url = "https://api.openai.com/v1/chat/completions"
    
    headers = {
        "Authorization": f"Bearer {API_KEY}",
        "Content-Type": "application/json"
    }

    data = {
        "model": "gpt-4o-mini",
        "messages": [
            {"role": "user", "content": message}
        ]
    }

    res = requests.post(url, headers=headers, json=data)

    if res.status_code != 200:
        print("Error:", res.text)
        return
    
    reply = res.json()["choices"][0]["message"]["content"]
    print("AI:", reply)


print("AI STARTED (type exit)")

while True:
    msg = input("You: ")
    if msg == "exit":
        break
    chat(msg)
