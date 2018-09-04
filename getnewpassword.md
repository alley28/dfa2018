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

To get a new Password, you must call an API.

The API Is provided as a REST API at this location:

Method Supported:  `POST`

Host:  `https://service.eu.apiconnect.ibmcloud.com`

Path: `gws/apigateway/api/7315e48f763e46c979de9efd37b971af2adecc3268d544ce0fe0232436dc8744/Fu6R9t/password`

Required Headers:
`Content-Type`:`application/json`

`Accept`:`application/json`

`X-IBM-Client-Id`:`1ec6da49-9bda-409e-8ea4-075870e952c2` 

Request Body: `[NONE]`

Response Body: 
```
{
"password":"somepassword"
}
```

Requests are HTTP POST Operations using JSON as Payload.  In order to call this API you can create a new API in App Connect.  To do that follow these instructions

1. Go to your browser.  You should already be authenticated into App Connect
2. Click on the `Dashboard` Heading if you aren't already there
3. Click on `+New` and then `Flows from an API`
4. APIs are model driven using App Connect.  A Model is simply a structure for the request/response payload used by the API.  In this case, there is no request body, and the response body is very simple (see Response body section above).
5. Give the model a name.  `Password` is fine. Click `Create Model` when complete.
6. You can now add properties to your model.  These will be the data elements that make up your model.  This model will only have 1 element.  Call it `password` and it will be of type `string`.
7. Click on the `Operations` tab.  You will now create an operation to call the Password API.
8. From the `Select Operations to Add` dropdown select `Create Password`.  Then click `Implement Flow`
9. This will take you to your flow screen.  You can add `operations` to your flow by clicking the `+` icon.  Do so now.
10. App Connect will then ask you what type of operation you would like to add.  From this point, you can see the large list of pre-configured connectors to applications (like Salesforce) and Technologies (Like Databases) as well as other APIs that might be exposed to you in your IBM Cloud organization and elsewhere.  For this step, under the `Applications` heading, use the context based search to find the `HTTP` operation by typing in `HTTP` into the search bar.
11. Click on the `Invoke Method` link to add the operation to your flow.  Click the `Connect` button twice to start the configuration process of this operation.  The first `Connect` you click will bring up basic authentication information and HTTP endpoint override options - you can skip that.
12. The next step is to configure the flow to call the Password Reset API.  Set the configuration settings as follows:
	* HTTP Method: `POST`
	* URL (Fully Qualified): `https://service.eu.apiconnect.ibmcloud.com/gws/apigateway/api/7315e48f763e46c979de9efd37b971af2adecc3268d544ce0fe0232436dc8744/Fu6R9t/password`
	* Request Headers: You will set three values: `Content-Type`, `Accept` and `X-IBM-Client-Id`.  Click on `Add Property` to add each one.  Set the values to string.  
	* You can then set the values as follows after clicking the `Edit Mappings` button. 
		* `Content-Type`:`application/json`
		* `Accept`:`application/json`
		* `X-IBM-Client-Id`:`bcf70dee-a288-4c99-872e-cc63fa49436d` 
13. Request body you can leave blank.
14. Set the `Continue Flow (non-2XX)` to the value of `true`.
14. On the main flow, click on the `Response` operation.
15. Map the Response body by clicking on the "Hamburger" icon on the far right hand side of the Response Body text box.  Here you can select the `Response Body` variable via the drop down from the `HTTP/Invoke Method`.
16. The configuration is now complete. Your changes are saved automatically.  Click `Done` to return to the dashboard
17. You can start up the flow by clicking the "3 dots" icon on the far right side of the screen and then selecting `Start API`
18. You should now see the API in the `Started`state.  You can now run it.  App Connect does have a test harness where you can run APIs you create.  Within the same view inside of your flow, at the top of the screen you should see two headings `Define` and `Manage`.  You created the flow already from within the `Define` section.  Click on the `Manage` tab to go into API Management mode.
19. From within the manage tab, there are a number of options how you can secure and manage the API you created.  For the moment, you can ignore these and scroll all the way to the bottom to the `Sharing Outside of Cloud Foundry organization` heading.  Click on the `Create API Key` buttom.  Give this key a name.  No need to copy and paste this key, as the test tool will automatically use that key when you test it.
20. Once the key has been created, a link will appear that contains the developer portal for your API.  This portal would normally be shared with others who wish to consume the API you just created from within their respetive applications.  For today, just click on this link and it will bring you to the portal page where the test client is.
21. Once you are in the portal, you will see some documentation for your API as well as the ability to export it as Open 2.0 compliant YAML.  For now, simply find the test tool by clicking on the `Try it`on the top right hand part of the portal page.
22. Leaving the default header parameters as is, as well as the request body blank, click on the `Call Operation` button.
23. If it completes successfully, you will have a password!  Go back to the Watson AI UI and then attempt to open the door again.