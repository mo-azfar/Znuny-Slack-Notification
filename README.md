# Znuny-Slack-Notification
- Znuny-Ticket-Notification-To-Slack-Users Via Webservices
- Required at least Znuny 6.1.x

		- This is only for Notification Owner Update.
		- For others kind of notification, kindly create another Invoker. You may refer existing invoker (OwnerUpdate) and existing HTTP::REST Configuration.


1. Create New Slack App. Reference: https://api.slack.com/apps

a) Create an App > From scractch
   - App Name: Anything
   - Workspace: Anything 


2. Create incoming webhooks via Your App Name > Add features and functionality > Create Incoming Webhook > Activate Incoming Webhooks


3. Create Bots via Your App Name > Add features and functionality > Bots > Review Scopes to Add

a) Bot Token Scopes > Add an OAuth Scope

		chat:write
		chat:write.customize
		chat:write.public
		im:write

b) OAuth Tokens for Your Workspace > Install to Workspace > Allow

c) **OAuth Tokens for Your Workspace > Bot User OAuth Token

E.g: xoxb-234234234-234234234324-hffghsgfhdfhdgfh

**Copy and save it somewhere first.


4. Import the 'Slack Notification.yml' via Admin > Web Services.

5. Update the Slack Bot User OAuth Access Token (3c) at the created webservice.

	a) OTRS as requester > Network transport (HTTP::REST) > Configure
	
	b) Authorization : Bearer SLACK_BOT_OAUTH_TOKEN
	
		E.g: Bearer xoxb-234234234-234234234324-hffghsgfhdfhdgfh

	c) Save and finish
	

6. Import and deploy ZZZAgentSlack.xml at /opt/otrs/Kernel/Config/Files/XML/

7. Obtain the Slack Member ID for the users, and update it into Agent Preferences > Miscellaneous > 'Slack Member ID'. 	

- Click on a user name within Slack.  
- Click on "View profile" in the menu that appears.  
- Click the more icon "..."  
- Click on "Copy Member ID."  


7. Create a new Ticket Notification  

		- Event: NotificationOwnerUpdate
		- Select Recipients: (Should be owners)
		- Select Notification Methods: Webservices 
			-- Web service name: Slack Notification
			-- Invoker: OwnerUpdate 
		
		- Notification Body and Text
			-- Anything as the actual value is set from XSLT itself.
		