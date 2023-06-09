# RV-01 (A simple chatbot with voice recognition!)
This Python script is a simple chatbot that uses the Google speech recognition API to listen to and transcribe spoken input. The chatbot reads from a JSON file (rules2a.json) that contains a set of rules for how to respond to certain phrases or commands. This gives the advantage of only to have to edit one file in order to add more commands (the json file).

## Dependencies
 * speech_recognition
 * pyttsx3
 * subprocess
 * json

## Usage
* Install the required packages by running pip install -r requirements.txt in the command line.
* Open the terminal and navigate to the directory containing the script file.
* Run the script by typing python chatbot.py in the command line.
* The chatbot will start listening to your voice input through your microphone.
* Say something and wait for the chatbot to respond.
* The chatbot will continue running until you stop the script manually.

## JSON file


The JSON file contains rule-based responses to specific user inputs or patterns. 

In this case, it's synthax is the following;

{    
    "pattern": "what is your name",    
    "response": "My name is Ar-vee O one."  
}

It will wait until it hears the pattern (A question) and will provide a response. However, in order to make it more functional, a "type" field indicating that they are command responses that trigger specific actions, such as opening or closing applications.

for example;

{
    "pattern": "open file browser",
    "response": "cmd:gnome-terminal -- mc &",
    "type": "cmd"
    
},

The response, has the prefix of "cmd:", indicating that the response is to be executed in a CLI. This gives the advantage of having the chatbot being able to start many applications and scripts.


## Functions
**recognize_speech()**
This function records audio from the microphone and uses the Google speech recognition API to transcribe the spoken input into text. If successful, it returns the transcribed text. Otherwise, it returns None.

**execute_command(command)**
This function takes a command as a parameter and executes it in the command line. If the command is successful, it returns the output of the command and a return code of 0. Otherwise, it returns an error message and the return code of the failed command.

**chatbot(text)**
This function takes a string of text as a parameter and checks if it matches any of the rules in the rules2a.json file. If a match is found, the chatbot follows the specified response in the rule, which could be a command to execute or a simple message to return. If no match is found, the chatbot returns a default message.

## Limitations
* This chatbot only works with English spoken input.
* The chatbot can only respond to phrases or commands that are specified in the rules2a.json file. It cannot handle any other requests.
* The chatbot's response may not always be accurate or appropriate, depending on the input it receives and the rules specified in the JSON file.

## TO-DO LIST
* Add more functions and responses.
* Have a wake-word that can be personalized.
* Have it use an offline speech recongnition (Sphinx).
