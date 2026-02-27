### week 2: SSH Basic (Day 1-2)

## what is SSH?

SSH (secure shell) allows logging into a remote Linux server securely.


Example :

```bash
ssh user@server-ip
```

### Bandit Practice Connection

ssh bandit0@bandit.labs.overthewire.org -p 2220

. bandit0 = username
. bandit.labs.overthewire.org  = server address
. -p 2220 = custom port

## Useful Commands After Login

. whoami

Shows current logged-in user.

. hostname

Shows server Machine name.

. pwd

Shows Current Directory path.

. ls

Lists files in the directory.

. cat

Read contents of the file.

# DevOps Lesson

Always confirm :

.User
.Server name
.Current Directory

Before Making Changes.
