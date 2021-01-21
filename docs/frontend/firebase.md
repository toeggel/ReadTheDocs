## Firebase setup (Angular App)
 - create firebase project online
 - 1st Time
	- npm install -g firebase-tools (if not already installed)
	- your-build-command-here (ng build --prod)
	- firebase login
	- firebase init
		- config as needded
			e.g.: simple angular hosting:
			- Are you ready to proceed? (Y/n) = Y
			- Which Firebase CLI features do you want to setup for this folder? = Hosting
			- Select a default Firebase project for this directory = Your-Firebase-Project-Name
			- What do you want to use as your public directory? = dist
			- Configure as a single-page app (rewrite all urls to /index.html)? (y/N) = Y
			- (File dist/index.html already exists. Overwrite? (y/N) = N)
	 - firebase deploy
	 - firebase open hosting:site
 - redeploy:
	- your-build-command-here (ng build --prod)
	- firebase deploy
 