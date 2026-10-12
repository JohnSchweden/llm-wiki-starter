# 2 Sync it

A GitHub account. The Git plugin. Push it, so it lives outside the laptop.

Goal: your wiki sits in a private GitHub repository and syncs on its own.

## Steps

- [ ] Create a free GitHub account at github.com/signup.
- [ ] Install Git.
  - macOS: type `xcode-select --install` in Terminal, or ask the agent to do it.
  - Windows: install Git for Windows from git-scm.com.
- [ ] Type: "Install the GitHub CLI and log me in with gh auth login." A browser window opens; sign in there.
- [ ] Type: "Make this folder a git repository, create a PRIVATE GitHub repository called my-wiki and push it." Keep it private: your profile lives in it.
- [ ] Open the repository on github.com and check that your notes are there.
- [ ] In Obsidian: Settings, Community plugins, Browse, search "Git", install the plugin by Vinzent, enable it.
- [ ] In the Git plugin settings, set the auto commit-and-sync interval to 30 minutes.

## Done when

- [ ] A note you change today shows up on github.com within the hour, without you doing anything.

Windows note: if the push fails with a permissions error, ask the agent to check Git Credential Manager. If skills stop working, Windows may need Developer Mode for symlinks.
