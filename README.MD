# Resume Chat

Publicly available deployed example:  
[boyko-chat.com](http://boyko-chat.com)

A Python web application that chats and answers questions about your resume.  
It uses EITHER the [OpenAI's Assistant API ](https://platform.openai.com/docs/assistants/overview)  
OR [Anthropic's Claude API via the Python SDK ](https://docs.anthropic.com/claude/reference/client-sdks)
Inspired by OpenAI's GPTs unavailability to non-plus users.  
Background - I created a Resume GPT and put the link to it on my resume, so folks can chat with it.  
It turned out only ChatGPT+ users could access GPTs.  
This is my workaround for that - wrap the Assistant API or Claude with a web app.  

For this thing to work with OpenAI's Assistant API, You'd need:
1. [OpenAI API key ](https://platform.openai.com/api-keys)
2. [OpenAI API Credits](https://platform.openai.com/account/billing/overview)(without giving OpenAI some money, the API calls won't work)

For this thing to work with Claude, You'd need:
1. [Anthropic API key](https://console.anthropic.com/account/keys)

## Setup and Installation

### Prerequisites

- Python 3.11 or higher
- pip

### Installing Dependencies

Run the following command to install the required packages:

```shell
pip install -r requirements.txt
```


## Running the Application

Replace the content of the config/data/Resume.txt file with your Resume.  
Replace the name in config/PersonConfig.json with yours.  
Update the Assistant's name, description and instructions config/AssistantConfig.json to your liking.  
If the above instruction does not make sense, you may want to check out the [Assistant API docs](https://platform.openai.com/docs/assistants/overview)  

The application creates an Assistant which can also be accessed from [OpenAI's platform UI](https://platform.openai.com/assistants).  
If you want to use an Assistant you have already created, you could just put the Assistant's id in config/assistant_id.txt.  

### local
The default `CHAT_PROVIDER` is "OpenAIChatProvider".   
If you'd like to use Anthropic's Claude instead,  
you'd want to set the `CHAT_PROVIDER` env var to "AnthropicChatProvider".  

Execute the following command to start the FastAPI server:

```shell
uvicorn main:app --reload
```

The application will be available at `http://127.0.0.1:8000`.

### Docker
build the image
```shell
docker build -t resume-chat .
```
start it up with an OpenAI backend
```shell
docker run -d -p 8099:80 -e OPENAI_API_KEY={you_openai_api_key} resume-chat
```

start it up with a Claude backend
```shell
docker run -d -p 8099:80 -e CHAT_PROVIDER=AnthropicChatProvider -e ANTHROPIC_API_KEY={you_anthropic_api_key} resume-chat
```

access it at `http://127.0.0.1:8099`.

## Usage

Just Chat Away

## Contributing

Unlikely that you will need to, but a PR would work

## License
I'd be psyched if you find this code useful. Do with it as you wish.


