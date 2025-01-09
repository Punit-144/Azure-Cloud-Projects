# Users, Groups, and MFA

### Task - 
In this particular task, we will create users and groups using Azure Active Directory (Azure AD) and then implement Multi-Factor Authentication (MFA).

### Steps to Create Test Users and Test Groups in Azure AD:

1. **Search for Azure AD Directory**:
   Open the search bar in the Azure portal and search for **"Azure Active Directory"**.

2. **Create Test Users**:
   - Navigate to **Users** on the left side of the Azure AD panel.
   - Click **New User**, then select **Create New User**.
   - Name the new user as **TestUser1**.
   - After deploying **TestUser1**, go to the **Assigned Roles** section and assign the role **"User Administrator"**.

3. **Create Another User**:
   - Repeat the above steps to create **TestUser2**.
   - **Note**: Remember the username and password for both users for future sign-in.

4. **Create Test Groups**:
   - In your **Default Directory**, go to **Groups**.
   - Click on **New Group**, provide a **Group Name**, and set the option to assign **Azure AD roles** to this group.
   - Assign **TestUser1** as **Group Owner** and **TestUser2** as **Group Member**. Click **Create**.

5. **Test Group Created**:
   - A new test group is now created and ready for use.

6. **Activate Free Trial for Azure AD Premium P2 License**:
   - Go to **Licenses** in the Default Directory, and click on **All Products**.
   - Select **Free Trial** and open **Roles and Administrators** to view assignments. **TestUser1** should be listed here.

---

### Implementing Multi-Factor Authentication (MFA):

1. **Enable MFA for TestUser1**:
   - In Azure Active Directory, go to **Users** and click on **Per-user MFA** in the navigation bar.
   - This will open the **MFA** tab. Select **TestUser1** and click on **Enable** on the right side. Confirm the action by clicking **Enable Multi-Factor Authentication**.

2. **Sign In with TestUser1**:
   - Sign in with the **TestUser1** user principal name and password.
   - After signing in, you will be redirected to a new page. Click **Next** and follow the prompts.

3. **Set Up Microsoft Authenticator App**:
   - Scan the displayed QR code using the **Microsoft Authenticator app** installed on your mobile device.
   - After scanning the code and adding the user in your Authenticator app, click **Next**.

4. **Verify Authentication**:
   - The Authenticator app will prompt you for a verification code. Enter the code displayed in the app.
   - If the correct code is entered, you will see a confirmation message. Click **Next** and then **Done**. This confirms that MFA has been successfully enabled for **TestUser1**.

5. **Enable MFA for Other Users**:
   - You can repeat the same process to enable MFA for all other users as needed.

---

### **Screenshots are available in the PDF** for a detailed walkthrough of these steps with visual references.

---

**Task Completed**.
