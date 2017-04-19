## Node Install
We will install node via [homebrew](http://brew.sh/). Brew is the *The missing package manager for macOS* meaning it allows us to install tools from the command line. The benefits of installing node with brew over the Node.js installer are outlined on this [blog](http://blog.teamtreehouse.com/install-node-js-npm-mac).

#### Steps
1. First you need to get brew. You can test if you have brew with this command:

	```
	$: which brew
	> /usr/local/bin/brew
	```
If you don't have it follow the install instructions on the [brew site](http://brew.sh/). You will need to run a run command in your terminal. Come find an instructor if you have permissions issues. 
2. Install node with brew using the following command:

	```
	$: brew install node
	```
It will think for awhile, but once it is done you should be able to test you have node with the `which node` command just as we did with brew above.

#### Resources
You many encounter permissions issues when installing packages with brew. Come get help from an instructor. Depending on what you are seeing the following stackoverflow post might be the answer:

[http://stackoverflow.com/questions/16432071/how-to-fix-homebrew-permissions?answertab=votes#tab-top](http://stackoverflow.com/questions/16432071/how-to-fix-homebrew-permissions?answertab=votes#tab-top)