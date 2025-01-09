# IIS-Web-Server Configuration

This folder contains the implementation of the Privileged Identity Management (PIM) task on Azure. It demonstrates the configuration and role assignment process in Azure, focusing on Just-in-Time (JIT) access, approval workflows, and multi-factor authentication for added security.

## Task Overview

The goal of this task was to configure Azure Privileged Identity Management (PIM) to manage and assign roles to users within the Azure subscription and Active Directory. Users must request access to certain roles, and the requests must be approved by an assigned global administrator before the roles are activated.

## Contents

1. [Objective of the Task](#objective-of-the-task)
2. [What is PIM](#what-is-pim)
3. [Key Features of PIM](#key-features-of-pim)
4. [Practical Implementation of the Task](#practical-implementation-of-the-task)
5. [Conclusion](#conclusion)
6. [References](#references)
7. [Screenshots](#screenshots)

## Objective of the Task

Perform a Privileged Identity Management task in Azure and assign roles to users. Users must request roles, and the request must be approved by an assigned approver before the role is activated.

## What is PIM

Privileged Identity Management (PIM) in Azure is a service that helps organizations manage and secure access to Azure resources. PIM enables the control and monitoring of high-level privileges for users who access critical resources, reducing the risk of unauthorized access and ensuring compliance with security requirements.

## Key Features of PIM

- **Just-In-Time (JIT) Access**: Assign time-bound, on-demand access to Azure roles to minimize continuous privileged access.
- **Approval Workflow**: Enforces an approval process where a global administrator must approve user role requests.
- **Privileged Role Auditing**: Tracks and logs privileged role activities for security and compliance monitoring.
- **Security Reports and Alerts**: Notifies administrators of suspicious activities related to privileged roles.
- **Azure AD Integration**: Seamlessly integrates with Azure Active Directory (Azure AD) to enhance identity and access management.

## Practical Implementation of the Task

### 1. Create a User

- Go to the Azure portal and create a new user.

### 2. Access Privileged Identity Management (PIM)

- In the Azure portal, search for "PIM" and navigate to **Azure AD Roles > Default Directory**.

### 3. Assign Roles

- In PIM, go to **Roles > User Administrator** and assign the appropriate role.
- Enable the "Require approval to activate" option and set up Multi-Factor Authentication (MFA) for added security.

### 4. Test User Login with MFA

- Log in as the test user and set up MFA using the Microsoft Authenticator app.

### 5. Request Role Activation

- The test user can now request activation of the **User Administrator** role by clicking on "Activate" under the "Eligible Assignments" section.
- The global administrator will receive an approval request in PIM.

### 6. Global Admin Approves Request

- The global administrator reviews and approves the request in the **Approve Requests** section.

### 7. Confirm Role Activation

- After approval, the test user's **User Administrator** role will move from "Eligible Assignments" to "Active Assignments."

## Conclusion

The implementation successfully ensures that any user created in the root subscription will require approval from a global administrator before they can use their assigned roles. This setup enhances security by utilizing Azure PIM's approval workflows and MFA.

## References

1. [OpenAI Chat](https://chat.openai.com) - For writing the Key Features part of this document.
2. [YouTube](https://www.youtube.com) - For learning about the implementation of this task.
3. [Azure PIM Documentation](https://learn.microsoft.com/en-us/azure/active-directory/privileged-identity-management/pim-resource-roles-assign-roles) - Official documentation for learning PIM.


## Screenshots

I have created a detailed PDF documentation that includes screenshots and step-by-step instructions for this task. You can refer to the document for a deeper understanding of the practical implementation and configuration steps.

