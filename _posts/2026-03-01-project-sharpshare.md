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

![image](https://private-user-images.githubusercontent.com/107306362/556958269-572b1ddc-edb7-4b39-bdba-817c18f0bcb6.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzI0NzY0MTksIm5iZiI6MTc3MjQ3NjExOSwicGF0aCI6Ii8xMDczMDYzNjIvNTU2OTU4MjY5LTU3MmIxZGRjLWVkYjctNGIzOS1iZGJhLTgxN2MxOGYwYmNiNi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwMzAyJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDMwMlQxODI4MzlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT00MzY0MWI5NjNiNGFmYWZlMTRiNjg2MDVlZDNmMWRhNzU4YmI4ZTkxYTNkMTM1YjYyOTg1OTgzODkyZWZjMzNkJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.7Q1r_szFjAobzJYrOznuriQ-1QTSo6FxHpadeU7v6Fw)

Security is fully detailed in [Security.md](https://github.com/Echostorm44/SharpShare/blob/master/Security.md)
## The Short Version

- Every session is protected by a **passphrase only you and your peer know**.
- All data travels over an **encrypted tunnel** — nobody in the middle can read your files.
- Both sides **verify each other's identity** before any files are exchanged.
- The connection is **direct, peer-to-peer** — no third-party server ever sees your data.
- Repeated incorrect passphrases trigger **automatic lockouts** to stop guessing attacks.
- Every file received is **integrity-checked** to ensure it arrived without corruption or tampering.