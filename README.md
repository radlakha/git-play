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

It all seems to point to cached credentials.   
Running `GIT_TRACE=1 git push origin main`   