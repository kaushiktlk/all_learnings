## Experience

 - Git throws this error when I try to git push or login:
   >Username for 'https://github.com': kaushiktlk
   >Password for 'https://kaushiktlk@github.com': 
   >remote: Support for password authentication was removed on August 13, 2021.
   >remote: Please see https://docs.github.com/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls for information on currently recommended modes of authentication.
   >fatal: Authentication failed for 'https://github.com/kaushiktlk/all_learnings.git/'
 - One solution is to create a Personal Access Token. Tha can be done by going to github in browser. Go to Settings > Developer Settings > Personal Access Tokens. Generate new token and copy the token.
 - Run the below command to enable git to store the PAT when you enter it the first time. From next time onwards, git will remember and take care of it for you. This is done by storing the credentials as a plaintext file in ~/.git-credentials file
   ```git config --global credential.helper store```
 - If you don't want it to be saved in a plaintext file, then use below command which does not save PAT in a plaintext file but the downside is that the token will be valid for a short period of time only(default is 15min).
   ```git config --global credential.helper cache```


