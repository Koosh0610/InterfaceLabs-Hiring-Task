INTERFACE LABS HIRING TASK

Task: An AI Agent to fill out a Google form based on natural language input.

An AI Agent to fill out a Google Form comes under the interessting application of using AI Agents to interact with web. An area of interest for many people.

Following are the steps to run it locally on your laptop or PC:

```git clone https://github.com/Koosh0610/InterfaceLabs-Hiring-Task.git```\
```cd InterfaceLabs-Hiring-Task```\
```pip install -r requirements.text```\
```python -m streamlit run streamlit_app.py```

I use ```gpt-4-turbo``` as the LLM. ```gpt-4o-mini``` is unsuccesful at the task and ```gpt-4o``` is costlier that ```gpt-4-turbo```

The project is an implementation of the research paper [WebVoyager](https://arxiv.org/abs/2401.13919).

The task to be executed is stored in a [json file](https://github.com/Koosh0610/InterfaceLabs-Hiring-Task/blob/main/data/task.jsonl).

Upon launch of the page, please enter your key in the sidebar on the streamlit page. The streamlit page will open in your default browser. The page will dislplay the state of the agent in the form of webpage screenshot. You can track the progress of the agent this way. Or you can open the ```results``` directory to see the process logs.

Action process:
We open a headless browser via Selenium. A javascript script is executed to annotate the page and form bounding boxes for the vLLM to recognise. Then a screenshot is taken which is passed to vLLM along with the prompt. A ReAct agent prompt is used to generate "Thought" and "Action" and based on "Observation". LLM decides to take an action based on the user instructions. The reasoning done by LLM are the thoughts and how to interact to with the page forms part of the action. It can form six actions as of now:
1. Click
2. Type
3. Scroll
4. Wait
5. GoBack
6. Google.
   

Modification to the task: The user input is modified a bit from my side. Raw input didn't allow the LLM to execute the actions properly. It has been shown that respond to [emotions](https://arxiv.org/abs/2307.11760) and hence the LLM is told that the user is sick and not in a state to fill out the form.

Limitations:

1. Write now the url to be navigated is hard coded into the task.
2. I couldn't figure out all the errors while using selenium with a streamlit page and hence input cannot be given on a GUI. So, it is mentioned seperately in a JSON file.

Future Work:
1. Give additional helper functions to simulate a human's use of the web
2. There are certain instances where pop-ups restrict the bot to work. Despite instructions to close the pop-ups, they fail at this task. Additional prompting methods/functions to solve this bug.
