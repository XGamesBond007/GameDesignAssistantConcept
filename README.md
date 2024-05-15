    DesignAssistantConcept/ # Directory
Package ├── objects/ # package
  Module│  M├── __init__.py
  Module│  M├── world.py        # Defines world objects by class: City , Town , Building , etc.
  Module│  M├── npc.py          # Defines npc objects by class: Guard, Trader, Enemy, etc.
  Module│  M├── dialogue.py     # Defines dialogue structures by class: Future implementation
  Module│  M├── guild.py        # Defines each Guild by class: TradingGuild, MiningGuild, etc.
  Module│  M├── quests.py       # Defines quest structures by class: Gather, Kill, SpeakTo, etc.
        │  M└── .py 
        │
Package ├── managers/ # game_manager is main
        │   ├── __init__.py
  Module│ *M├── game_manager.py         # Calls Functions from all remaining managers.
  Module│  M├── world_manager.py        #  Defines all functions related to the world_manager.
  Module│  M├── guild_manager.py        #  Defines all functions related to the guild_manager.
  Module│  M├── npc_manager.py          #  Defines all functions related to the npc_manager.
  Module│  M├── quest_manager.py        #  Defines all functions related to the quest_manager.
  Module│  M└── dialogue_manager.py     #  Defines all functions related to the dialogue_manager.
        │
        │
Package ├── data_handling/ # Stores the data of all included packages.
        │   ├── __init__.py # imports game_data.py for all other packages to communicate
  Module│ *M└── game_data.py
        │
        │
Package ├── utilities/
        │   ├── __init__.py
  Module│  M├── converters.py
  Module│ *M└── helpers.py
        ├── main.py
        └── __init__.py
================================================ Breakdown ============================================================
Here's a breakdown of each directory and file:

objects/:       Stores classes in sorted modules. Each class defines a specific object.
     __init__.py:   Allows data_handler to edit class instances in all .py files from objects/
        world.py:   Stores world structures as classes. City , Town , Building
          npc.py:   Future implementation of NPC classes.
     dialogue.py:   Future implementation of Dialogue classes.
        guild.py:   Future implementation of Guild classes.
        quest.py:   Future implementation of Quest classes.
effect_system.py:
 magic_system.py:

managers/:      Contains modules implementing managers for each entity type to handle operations.
    __init__.py:   create,view,edit,delete class instances stored inside game_data.py
       world_manager.py:  Create, View, Edit, Delete class instances from objects/world.py
        npc_manager.py:   Future implementation of NPC classes.
   dialogue_manager.py:   Future implementation of Dialogue classes.
      guild_manager.py:   Future implementation of Guild classes.
      quest_manager.py:   Futur Implementation of Quest Classes.

data_handling/: Contains modules for data handling operations, such as saving and loading data.
    game_data.py: Access all data.py files in this folder to give access to managers/
    world_data.oy: Stores all class instances related to

utilities/: Contains modules for utility functions or classes used across the application.
    converter.py: implemented later. Converts all data to json or word docs for users to print
    helpers.py : implemented later.

main.py: The main program module, responsible for the program's entry point and user interface.
   role: main.py should give the impression of an assistant that speaks to users.

     ex: "Assistant: Hello user, Welcome to the program where would you like to begin?"
         between assistant prompts and user inputs we should be able to run nearly
         every function inside the program.

   Access: main.py should only need to communicate with managers/game_manager

   game_manager.py should then handle all function calling inside the program.

Project logic flow:
UserInput -> directory/main.py
directory/main.py -> managers/game_manager.py
managers/game_manager.py -> data_handling/game_data.py
data_handling/game_data.py -> objects/(all .py files)
objects/(all .py files) -> all class instances and functions
