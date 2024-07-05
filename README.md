# Granting Access to External Organization Groups

This repository provides a detailed guide on how to grant access to external organization groups using Google Admin Console and Google Cloud Platform.

## Step 1: Create a Group in the Source Organization

1. **Sign in to Google Admin Console**:
   - Open the [Google Admin Console](https://admin.google.com/).
   - Sign in with an account that has the necessary administrative privileges.

2. **Navigate to Groups**:
   - From the Admin console Home page, go to Groups.

3. **Create a New Group**:
   - Click on **Create group**.
   - Enter the group details:
     - **Group Name**: e.g., `DevAdmin`
     - **Group Email**: e.g., `devadmin@example.com`
     - **Group Description**: (optional)
   - Click on **Next**.
   - Configure group settings as needed (who can join, post, view topics, etc.).
   - Click on **Create group**.

## Step 2: Add Members to the Group

1. **Go to the Group**:
   - In the Google Admin Console, navigate to Groups.
   - Click on the group you just created (e.g., `Developers`).

2. **Add Members**:
   - Click on **Add members**.
   - Enter the email addresses of the users you want to add.
   - Click on **Add to group**.

## Step 3: Grant the Group Access to Resources in the Target Organization

1. **Identify the Resource in the Target Organization**:
   - Determine the resource (e.g., project, bucket) in the target organization that the group from the source organization needs to access.

2. **Grant IAM Roles to the Group**

### Using the Google Cloud Console:

1. **Navigate to the IAM Page**:
   - Open the [Google Cloud Console](https://console.cloud.google.com/).
   - Go to the **IAM & Admin** page of the specific resource in the target organization (e.g., a project).

2. **Add the External Group**:
   - Click on **Add**.
   - In the **New principals** field, enter the email address of the group from the source organization (e.g., `developers@external-organization.com`).
   - In the **Select a role** dropdown, choose the appropriate role(s) you want to grant to the group.
   - Click **Save**.

### Using gcloud CLI:

1. **Open a Terminal**:
   - Ensure you have the `gcloud` CLI installed and configured with the necessary permissions.

2. **Add the Group to the IAM Policy**:
   - Use the following command to grant a role to the group on the specific resource (e.g., a project):

```sh
gcloud projects add-iam-policy-binding TARGET_PROJECT_ID \
  --member="group:developers@external-organization.com" \
  --role="roles/desiredRole"
