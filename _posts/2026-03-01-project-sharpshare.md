---
layout: post
title: "SharpShare"
categories:
  - Projects
tags:
  - sharpshare
  - avalonia
  - file sharing
  - p2p
  - csharp
---

[Github page](https://github.com/Echostorm44/SharpShare)

# SharpShare

SharpShare came from a frustration in trying to share a bunch of large files regularly with user's who are not technically savvy and just want it to work.  The project does the heavy lifting to open a port but keeps the entire process as secure and private as it can be. 

The process is simple.  

- Both users start the applicaiton and select a folder to share. Nothing outside that folder is visible to the other party.  
- One person decides to play host and the program discovers their IP and generates a secure pass phrase to give to the other party, the users are directly connected and all traffic between them is encrypted. 
- Both users can see the contents of each other's shared folders and can download anything from those folders they wish.  

The [SharpShare.zip](https://github.com/Echostorm44/SharpShare/releases/download/v1.0/SharpShare.zip) file in Releases can simply be unzipped somewhere and run as a portable program, it has no requirements and there is no installer.

<img width="1054" height="804" alt="image" src="https://github.com/user-attachments/assets/394f5bc5-ca86-4cd4-9bbf-adc8f2a6c71e" />

Security is fully detailed in [Security.md](https://github.com/Echostorm44/SharpShare/blob/master/Security.md)
## The Short Version

- Every session is protected by a **passphrase only you and your peer know**.
- All data travels over an **encrypted tunnel** — nobody in the middle can read your files.
- Both sides **verify each other's identity** before any files are exchanged.
- The connection is **direct, peer-to-peer** — no third-party server ever sees your data.
- Repeated incorrect passphrases trigger **automatic lockouts** to stop guessing attacks.
- Every file received is **integrity-checked** to ensure it arrived without corruption or tampering.
