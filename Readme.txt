# Restaurant ChatBot


## Pre-requisites

- python 3.7.0 and dependencies


## Installation

Create a new vitual python env:

	1.	""" conda create -n rasa python==3.7.0 """


### RASA
	2.	Run the Envsetup file which contains all dependencies for this bot to running
		From root directory run below
		"""
		pip install -r envsetup.txt
		"""

### Spacy

	1. Package Installation if spacy is not istalled from step2 above : envsetup.txt file then run below 
   """  pip install -U spacy  """

	3. Model Installation : run 
   """   python -m spacy download en_core_web_md   """

	4. Create custom shortcut link to Spacy model
   """ python -m spacy link en_core_web_md en   """


### Data Files

- **data/nlu/nlu.md** : contains training examples for the NLU model  
- **data/core/stories.md** : contains training stories for the Core model  


### Config Files

- **config.yml** contains model configuration and custom policy
- **domain.yml** defines chatbot domain like entities, actions, templates, slots  
- **smtpconfig.txt** contains SMTP server configuration information (_If using GMAIL, setup account and generate app password_) .

## Usages

- Train ONLY NLU model and validate

1.  """  python nlu_train_model.py --shell  """  : this is to test api ref; no need to use for chatbot working 


Step 1:
- Test generated NLU model (_generated NLU model should be available in 'models' folder prior to test_). 2 options are available:
  - DEFAULT : separate test set is created
  - VALIDATION : uses cross - validation
  
  """  python nlu_test_model.py --type DEFAULT
	   python nlu_test_model.py --type VALIDATION
  """

Step 2:
- Run RASA action server ( mandatory step to interact with chatbot) 

  """  python actions_server.py  """
 
Step 3: 
- Train RASA  model

  """  python dialogue_management_model.py  """

 
 Step 4:
- Starts an interactive session with restaurant chatbot

  """python  dialogue_management_model.py --shell  """


---
