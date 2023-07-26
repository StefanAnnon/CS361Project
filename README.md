# CS361 Project
Artemiy Arzumanov's Summer 2023 repository.

## 1. Individual Project
The assets zip contains all the scripts, graphics, prefabs, scenes, etc. created for the CS361 individual project. To recreate, create a new Unity 2021 project and replace the assets folder.

## 2. Microservice for Promptle
This microservice runs forever on http://flip2.engr.oregonstate.edu:42067/, which you will need to access via your OSU VPN. For the purposes for the contract, we will be using this FLIP server.
As a backup, the zip file contains a version you can run locally, via http://localhost:3000/. Make sure to use npm install to install the required dependencies!

### Description
The microservice will receive a user guess and a prompt, and send back the index(es) of the guess matching the prompt. It will also match “close enough” words like “cant” and “Can't”.

### Request
To REQUEST data, you must send a POST request to the provided URL containing a JSON object with a prompt and user_guess in the body. An example request body looks like this:

{
  "prompt": ["Write", "me", "a", "haiku", "about", "loafers."],
  "user_guess": "me"
}

Specifically, the prompt must be an array of strings, and the user_guess must be a single word string.

### Response

You will RECIEVE a response to your request as with the indexes of all the matches between the user_guess and the prompt as a JSON object in the body. The microservice ignores capitalization and special characters, so "loafers." in the prompt will match to a user_guess of "LOAFERS". An example response looks like this:

{
    "indexes": [1]
}

Specifically, indexes is an array of integers. There can be 0 to many matches to a user guess. An incorrect guess returns an empty array.

### UML Diagram

![image](https://github.com/StefanAnnon/CS361Project/assets/58959555/d5c008d1-7d25-47cf-b64d-2612ede2ff71)
