---
title: GetNewPasswordAPI
toc: false
sidebar: labs_sidebar
folder: master
permalink: /getNewPasswordAPI.html
summary: api docs
applies_to: [developer,administrator,consumer]
---

# API DOCUMENTATION AND TUTORIAL - GET A NEW PASSWORD
===============

## Document Sample (c) 2218 Cryocorp LLC

***WARNING - DO NOT USE WITHOUT PROPER AUTHORIZATION*** 

To generate a new Password, you must retrieve it from a database

The password resides in a Cloudant NoSQL Database on IBM Cloud. You will use App Connect running on IBM Cloud to complete this task. Instructions are provided below:

1. Go to your browser. You should already be authenticated into App Connect
2. Click on the `Dashboard` header if you aren't already there
3. Click on `New (+)` and then `Flows for an API`
4. APIs are model driven using App Connect. A Model is simply a structure for the request/response payload used by the API.  In this case, there is no request body since it is a GET, and the response body is very simple, containing just one field which we will create here shortly.
5. Give the model a name. e.g., `Password`. Click `Create Model` when complete.
6. You can now add properties to your model. These will be the data elements that make up your model. This model will only have 2 elements. Create the first one and call it `key` and set it to be of type `string`. You will see that the `ID` radio button to this property's immediate right is enabled. This will allow us to map in a URL parameter within our flow to allow us to extract the property item from the database. Create a second property and call it `password` and set it to be of type `string`.
7. Click on the `Operations` tab. You will now create an operation to call the Password API.
8. From the `Select Operations to Add` dropdown select `Retrieve password by ID`. Then click `Implement Flow`
9. This will take you to your flow screen. You can add `actions` to your flow by clicking the `+` icon. Do so now.
10. App Connect will then ask you what type of operation you would like to add. From this point, you can see the large list of pre-configured connectors to applications (like Salesforce) and technologies (Like Databases) as well as other APIs that might be exposed to you in your IBM Cloud organization and elsewhere. For this step, under the `Applications` heading, use the context based search to find the `IBM Cloudant` database operations by typing in `Cloudant` into the search bar.
11. Click on the `Retrieve Documents` link to add the operation to your flow. **Note** The proper IBM Cloudant Database has already been configured inside of your App Connect instance, so there is no need to enter in any connectivity parameters.
12. The next step is to configure the `IBM Cloudant Retrieve Documents` operation. The first step is to assign the database.  Using the drop down, select the `vaultdoorpwd` database
14. Click `Add Condition` and in the `Where` clause section, via the drop down select the `Document ID` column on the left hand side. Place your cursor in the field to the right of the `equals` drop down, and click on the "hamburger" icon to choose the `key` passed into the API.  You can retrieve the proper key in the following step.
15. You will need to enter in the proper Door ID key in order to retrieve the proper password.  Using the Watson UI, ask Watson what the `door id` is.  Copy and Paste the value Watson gives you as the `key` for the condition.
15. Where it asks for the `Maximum number of items to retrieve`, leave the default value of `1`.
16. Under the `If limit is exceeded` section, select the `Process 1 item from the collection` option.
17. Under the `If no items are found` section. Select the `Continue the flow and issue a 204: no content status code` options.
18. Immediately to the right of the IBM Cloudant operation, click on the `+` icon and add a `JSON Parser` operation. You can find this operation under the `Toolbox` heading. We will use this operation to parse the JSON object stored in the Cloudant Database.
19. Select the `JSON Input` to parse by clicking on the text box and clicking the "hamburger" icon. From the `Available Inputs`, select the `IBM Cloudant/Retrieve documents` dropdown and select the `Document Data` object.
20. Click the twisty arrow to reveal the `Output Schema` section.   Enter in the following sample JSON snippet:
```
{
 "password": "somepassword"
}
```
16. Click the `Generate Schema` button to have App Connect generate the JSON schema based on the sample provided above.
17. Lastly, configure the `Response` object by clicking on it. Under the `Response body` section, select the text box for the `password` field. Click on the "hamburger" icon and from the `Available inputs` heading, select the `JSON Parser/Parse` drop down and click on the `password` object.
17. The flow configuration is now complete. Your changes are saved automatically. Click `Done` to return to the dashboard.
17. You can start up the flow by clicking the "3 dots" icon on the far right side of the screen and then selecting `Start API`
18. You should now see the API in the `Started`state. You can now run it. App Connect includes the capability to manage and run APIs you create. Within the same view inside of your flow, at the top of the screen you should see two headings `Define` and `Manage`. You created the flow already from within the `Define` section. Click on the `Manage` tab to go into API Management mode.
19. From within the manage tab, there are a number of options how you can secure and manage the API you created. For the moment, you can ignore these and scroll all the way to the bottom to the `Sharing Outside of Cloud Foundry organization` heading. Click on the `Create API Key` buttom. Give this key a name. No need to copy and paste this key, as the test tool will automatically use that key when you test it.
20. Once the key has been created, a link will appear that contains the developer portal for your API. This portal would normally be shared with others who wish to consume the API you just created from within their respetive applications. For today, just click on this link and it will bring you to the portal page where the test client is.
21. Once you are in the portal, you will see some documentation for your API as well as the ability to export it as OpenAPI 2.0 compliant YAML. For now, simply find the test tool by clicking on the `Try it` on the top right hand part of the portal page.
22. You will note under the Parameters heading, you will see a text box for the `id` field. This will be the place where you will enter in the specific door id for which to get your password (as there are many doors at this facility).
23. Return to the Watson AI UI and ask Watson what the `Door id` is. It will return a value back to you. Copy and paste this value into the `id` value in the portal test tool.
22. Leaving the default header parameters as is, as well as the request body blank, click on the `Call Operation` button.
23. If it completes successfully, you will have a password!  Go back to the Watson AI UI and then attempt to open the door again.
