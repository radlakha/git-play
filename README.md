# git-play
Playground for git commands
This repo is like a scratchpad for git commands. You can use it to test out different git commands and see how they work.

Commit author should be personal but push may not work.
I'm surprised that I can push to this repo.

Test 001

Test 002

Test 003 logged out and cloned again from another account

Test 004 logged out from github browser account

Test 005 Turned on one more flag under Branch Protection Rules

Test 006 Laptop rebooted

Test 007 Switched to rulesets

Test 008 Rulesets worked with Bypass for adming. Confirm by switching to work account

Test 009 Bypass allowed other user too. Keep the bypass on and log out from the owner account on terminal (not just switch) and then push. It should fail.

Test is that owner should be able to push to main. Anyone else should fail.  
Then test that non-owner can push to a new branch and raise a PR that can only be merged by owner.

Test 010 Bypass setting changed to `Allow for pull requests only`  
This restricts everyone, including the owner, from pushing to main!  

On my public repo, I find that everyone can push to main. I tested this by logging out using `gh auth logout` Even though I have not added any collaborators and the screen says:  
`Direct access  
0 collaborators have access to this repository. Only you can contribute to this repository.`  
If I create a ruleset preventing push directly and require a pull request, then even I logged in is required to create a pull request, which is frustrating. Adding Bypass for Repo admin role then allows all, even those not logged in, to push. What am I doing wrong? 

Logged out `gh auth logout`
Cleared git cache with `git credential-cache exit` and `git credential-cache clear`  
Bypass setting changed to `Always Allow` for Repo Admin role.  

Quit the terminal in VS Code and also the terminal app. 

Test 011
It all seems to point to cached credentials.   
Running `GIT_TRACE=1 git push origin main`   
  
Above test showed that the push was allowed because of the cached credentials.    
To further confirm this I am creating a new user on github and trying to push to the repo using this new user.  

Step-by-Step  
Get or Create a Personal Access Token for the Test Account:  
Log in to the secondary GitHub account in a browser (use incognito mode to avoid conflicts with your primary account).  
Go to Settings > Developer settings > Personal access tokens > Tokens (classic).  
Click Generate new token:  
Name: “Test Push Token”  
Expiration: Set to 1 day (or shortest available).  
Scopes: Select repo (full control of private/public repositories).  
Generate the token and copy it (e.g., ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx).  
Note the username of the secondary account (e.g., testuser).  
Modify the Remote URL to Include Credentials:  
In your local repository, set the remote URL to include the username and token:  
bash  

Copy  
git remote set-url origin https://testuser:ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx@github.com/owner/repo.git  
Replace testuser with the secondary account’s username.  
Replace ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx with the token.  
Replace owner/repo with your repository’s owner and name (e.g., yourusername/yourrepo).  
Test the Push.  

PASSED!  
So credentials helper and or cached credentials are the issue.

Test user was added as a collaborator. And now it  is prompted to create a pull request.  
After creating a pull request, the test user was able to merge the pull request.