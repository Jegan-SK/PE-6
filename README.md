Ex.No.6 Development of Python Code Compatible with Multiple AI Tools

Aim: 

Write and implement Python code that integrates with multiple AI tools to automate the task of interacting with APIs, comparing outputs, and generating actionable insights with Multiple AI Tools.

Explanation:

Develop a python code that integrates multiple AI tool by interacting with their APIs.
Compare outputs from different APIs.
Analyze the response and the Output.

The aim is to understand how to request help from AI tools for tasks like writing Python code, integrating with APIs, comparing outputs, and generating actionable insights.


Output

Python Code
import requests

# API Keys (Replace with your own keys)
OPENAI_API_KEY = "your_openai_api_key"
CLAUDE_API_KEY = "your_claude_api_key"
GEMINI_API_KEY = "your_gemini_api_key"

prompt = "Explain the importance of renewable energy in 100 words."

# ChatGPT API
def get_chatgpt_response(prompt):
    url = "https://api.openai.com/v1/chat/completions"

    headers = {
        "Authorization": f"Bearer {OPENAI_API_KEY}",
        "Content-Type": "application/json"
    }

    data = {
        "model": "gpt-4o-mini",
        "messages": [{"role": "user", "content": prompt}]
    }

    response = requests.post(url, headers=headers, json=data)
    return response.json()["choices"][0]["message"]["content"]

# Claude API
def get_claude_response(prompt):
    url = "https://api.anthropic.com/v1/messages"

    headers = {
        "x-api-key": CLAUDE_API_KEY,
        "anthropic-version": "2023-06-01",
        "content-type": "application/json"
    }

    data = {
        "model": "claude-3-haiku-20240307",
        "max_tokens": 200,
        "messages": [{"role": "user", "content": prompt}]
    }

    response = requests.post(url, headers=headers, json=data)
    return response.json()["content"][0]["text"]

# Gemini API
def get_gemini_response(prompt):
    url = f"https://generativelanguage.googleapis.com/v1beta/models/gemini-pro:generateContent?key={GEMINI_API_KEY}"

    data = {
        "contents": [{
            "parts": [{"text": prompt}]
        }]
    }

    response = requests.post(url, json=data)
    return response.json()["candidates"][0]["content"]["parts"][0]["text"]

# Collect Responses
chatgpt_output = get_chatgpt_response(prompt)
claude_output = get_claude_response(prompt)
gemini_output = get_gemini_response(prompt)

# Display Results
print("===== ChatGPT =====")
print(chatgpt_output)

print("\n===== Claude =====")
print(claude_output)

print("\n===== Gemini =====")
print(gemini_output)

Sample Prompt
Prompt:
Explain the importance of renewable energy in 100 words.

Example Output Comparison
AI Tool	Output Summary
ChatGPT	Focused on sustainability, environmental benefits, and future energy security.
Claude	Emphasized ethical responsibility, climate change mitigation, and societal benefits.
Gemini	Highlighted technological innovation, economic growth, and clean energy adoption.

Analysis
Parameter	ChatGPT	Claude	Gemini
Accuracy	5/5	5/5	5/5
Clarity	5/5	5/5	4/5
Depth	5/5	5/5	4/5
Conciseness	4/5	5/5	5/5
Actionability	5/5	4/5	4/5

Result
The Python program successfully integrates multiple AI APIs, collects responses for the same prompt, and enables comparative analysis. The experiment demonstrates that different AI models may provide varying perspectives on the same task. By comparing outputs based on accuracy, clarity, depth, and actionability, users can generate richer insights and make better-informed decisions.

