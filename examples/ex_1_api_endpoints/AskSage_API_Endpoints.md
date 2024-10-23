# Ask Sage API Endpoints

<p align="center">
<img src="images/api_interface.png" width="650" alt="LLM Comparison Process">
</p>

## API Endpoints Overview

The Ask Sage API is documented using Swagger, which provides detailed information about the available endpoints, request parameters, response formats, and authentication methods.

### User API:
- Documentation: https://app.swaggerhub.com/apis-docs/NICOLASCHAILLAN_1/user-api/1.0
- The Base URL for the User API is: [ Base URL: https://api.asksage.ai/user/]

> The following table shows the available endpoints in the User API:

<center>

| Endpoint | Description |
|:---:|:---:|
| /get-token-with-api-key | Get an access token with API Key and email |
| /get-user-logins | Get your last logins (limited to 5 by default) |
| /get-user-logs | Get your last prompts |
| /add-dataset| Add a new dataset |
| /delete-datasets| Deletes a dataset |
</center>

Append the Base URL with the endpoint to interact with the Ask Sage API. Example https://api.asksage.ai/user/add-dataset

### Server API: 
- Documentation: https://app.swaggerhub.com/apis-docs/NICOLASCHAILLAN_1/server_ask-sage_api/1.0
- The Base URL for the Server API is: [ Base URL: https://api.asksage.ai/server/]

This information is used to interact with the Ask Sage API. The user can query models, select/get personas, get datasets, train models and more. 

> The following table shows the available endpoints in the Server API:

<center>

| Endpoint | Description |
|:---:|:---:|
| /get-models | Returns a list of available models via the Ask Sage services |
| /query | Main endpoint for generating completions based on the user's input |
| /query_with_file | Query with file endpoint for generating completions based on the user's input |
| /follow_up_questions | Endpoint for generating follow-up questions based on the user's input |
| /tokenizer | Endpoint for getting tokens of string value |
| /get-personas | Endpoint for getting the tokens of string | 
| /get-datasets | Returns a list of available datasets |
| /get-plugins | Returns a list of available plugins |
| /get-train | Trains the model based on the user's input |
| /file | Converts a supported file to plain/text |
</center>

Append the Base URL with the endpoint to interact with the Ask Sage API. Example https://api.asksage.ai/server/get-models

##  Ask Sage Python Client Endpoints

The Ask Sage Python client is documented and managed via the following link Python API Client: https://pypi.org/project/asksageclient/

###  API Endpoints

Note these are the ones available in the Python client as of the time of writing. 

<center>

| Function Name               | Description                                           |
|-----------------------------|-------------------------------------------------------|
| `get_models`                | Get the available models from the Ask Sage service.   |
| `add_dataset`               | Adds a new dataset                                    |
| `append_chat`               | Appends a chat to a chat history                      |
| `delete_dataset`            | Deletes a specified dataset                           |
| `assign_dataset`            | Assigns a dataset                                     |
| `get_user_logs`             | Retrieves all logs for user                           |
| `get_user_logins`           | Retrieves login information for a specific user       |
| `query`                     | Interact with the /query endpoint of the Ask Sage API. |
| `query_with_file`           | Executes a query using a file                         |
| `query_plugin`              | Executes a query using a specific plugin              |
| `execute_plugin`            | Executes a plugin with the provided content           |
| `follow_up_questions`       | Interact with the /follow-up-questions endpoint of the Ask Sage API. |
| `tokenizer`                 | Interact with the /tokenizer endpoint of the Ask Sage API. |
| `get_personas`              | Get the available personas from the Ask Sage service. |
| `get_datasets`              | Get the available datasets from the Ask Sage service. |
| `get_plugins`               | Get the available plugins from the Ask Sage service.  |
| `count_monthly_tokens`      | Get the count of monthly training tokens spent for this user from the Ask Sage service.|
| `count_monthly_teach_tokens`| Counts the number of teach tokens used in a month     |
| `train`                     | Train the model based on the provided content.        |
| `train_with_file`           | Train the dataset based on the provided file.         |
| `file`                      | Upload a file to the Ask Sage service.                |
</center>

Get Started and Navigate to the jupyter notebook example going through all the endpoints [![Open File](https://img.shields.io/static/v1?message=Open%20File%20&logo=github&labelColor=grey&color=blue&logoColor=white&label=%20)](asksage_python_client_overview.ipynb)  

## Leave a Comment
If you have any questions or comments, please feel free to let us know. We would love to hear from you!

Happy coding! 🚀