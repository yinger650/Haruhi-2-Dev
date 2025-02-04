## ChatHaruhi2.0的测试项目

主要用于开发和测试ChatHaruhi2.0

主要是原项目太大了每次clone和测试太慢

这个项目会在2.0初步功能开发完成后关闭。

请大家回去找原项目 https://github.com/LC1332/Chat-Haruhi-Suzumiya


# ChatHaruhi2.0的文档

## 初步使用

目前ChatHaruhi可以使用pip直接安装

```shell
pip -q install chatharuhi
```

依赖的库为

```shell
pip -q install transformers openai tiktoken langchain chromadb zhipuai
```

安装完成之后可以使用语法糖直接调用

这个例子见[notebook](https://github.com/LC1332/Haruhi-2-Dev/blob/main/notebook/test_GLMPro.ipynb)

```python
from chatharuhi import ChatHaruhi

chatbot = ChatHaruhi( role_name = 'haruhi',\
                      llm = 'openai')

response = chatbot.chat(role='阿虚', text = '我看新一年的棒球比赛要开始了！我们要去参加吗？')
print(response)
```

这就可以直接进行调用了。更完整的用法，是分开对system_prompt和story_db进行设置

这个例子见[notebook](https://github.com/LC1332/Haruhi-2-Dev/blob/main/notebook/test_LangChainOpenAILLM.ipynb)

```shell
wget -q https://github.com/LC1332/Haruhi-2-Dev/raw/main/data/characters/haruhi/haruhi.zip
unzip -q haruhi.zip -d /content/new_output
```

先下载和解压对应的文件，然后使用更完整的初始化方法

```python
from chatharuhi import ChatHaruhi

db_folder = '/content/new_output/content/haruhi'
system_prompt = '/content/new_output/content/system_prompt.txt'

chatbot = ChatHaruhi( system_prompt = system_prompt,\
                      llm = 'openai' ,\
                      story_db = db_folder)

response = chatbot.chat(role='阿虚', text = 'Haruhi, 你好啊')
print(response)
```

这样就可以使用了。如果你的人物还没有抽取story_db，可以使用这个方法去初始化

这个例子见[notebook](https://github.com/LC1332/Haruhi-2-Dev/blob/main/notebook/test_PrintLLM.ipynb)

```python
from chatharuhi import ChatHaruhi

text_folder = '/content/Haruhi-2-Dev/data/characters/haruhi/texts'

system_prompt = '/content/Haruhi-2-Dev/data/characters/haruhi/system_prompt.txt'

chatbot = ChatHaruhi( system_prompt = system_prompt,\
                      llm = 'debug' ,\
                      story_text_folder = text_folder)

chatbot.chat(role='阿虚', text = 'Haruhi, 你好啊')
```

这个时候chatbot会自动抽取text_folder中的embedding，时候还可以用

```python
chatbot.save_story_db('/content/haruhi')
```

的方式保存chormaDB到文件夹，下次就不用重新抽取了。基础的用法介绍到这里。后面是更详细的章节

## ChatHaruhi Gradio 2.0的部署

## 不同LLM的支持

## 目前支持的角色

## Embedding模型

## 改变ChatBot的记忆

## 后处理

