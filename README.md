# Gmail Cleanup Script

This Python script helps you clean up your Gmail account by searching for and deleting/unsubscribing from unwanted emails based on specified keywords.

## Prerequisites

- Python 3.6 or higher
- A Gmail account with the Gmail API enabled

## Installation

1. Clone the repository:
"""
git clone https://github.com/yourusername/gmail-cleanup.git
cd gmail-cleanup
"""

2. Install the required Python packages:
"""
pip install -r requirements.txt
"""


3. Set up the Gmail API:

- Go to the [Google Cloud Console](https://console.developers.google.com/).
- Create a new project or select an existing one.
- In the Dashboard, click on "Enable APIs and Services."
- Search for "Gmail API" and enable it.
- Go to the "Credentials" tab and click "Create credentials."
- Select "OAuth client ID."
- Choose "Desktop app" as the application type, give it a name, and click "Create."
- Download the JSON file containing your client secret by clicking the download icon next to your newly created OAuth client ID.
- Rename the downloaded JSON file to "client_secret.json" and place it in the repository's root directory.

4. Create a configuration file named "config.yaml" in the repository's root directory. Add the following contents to the file:

```
gmail_api:
  client_id: "YOUR_CLIENT_ID"
  client_secret: "YOUR_CLIENT_SECRET"
  redirect_uris:
    - "urn:ietf:wg:oauth:2.0:oob"
    - "http://localhost"
  token_uri: "https://oauth2.googleapis.com/token"
  auth_uri: "https://accounts.google.com/o/oauth2/auth"
label_id: "INBOX"
keywords:
  - "unsubscribe"
```
Replace YOUR_CLIENT_ID and YOUR_CLIENT_SECRET with the appropriate values from the "client_secret.json" file.

## Usage

Run the script using the following command:
python script.py

## Optional Command-Line Arguments

You can use command-line arguments to modify the script's behavior. Here are some examples:

    -To process emails with a different label, use the --label flag, followed by the label ID:
    ```
    python script.py --label LABEL_ID
    ```
    
    -To specify additional keywords or change the existing ones, use the --keywords flag, followed by a space-separated list of keywords:
    ```
    python script.py --keywords keyword1 keyword2 keyword3
    ```
    
    -To run the script without actually deleting any emails (dry run), use the --dry-run flag:
    ```
    python script.py --dry-run
    ```
    
    -To save the list of deleted email subjects to a file, use the --save-to-file flag, followed by the filename:
    ```
    python script.py --save-to-file deleted_emails.txt
    ```
    
    -For more information on the available command-line arguments, run:
    ```
    python script.py --help
    ```
