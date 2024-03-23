# Darkness Studio Workflow
## Workflow can help you:
- Create fluidity in work routines
- Organize daily tasks
- work closed
- Generate productivity and agility in employees’ workflow
- Reduce time spent on activities
- Reduce the possibility of errors
- Increase team productivity
- Considerably reduce human errors
- Greater focus on activities that generate more value for the company
- Workflow can be expressed in a series of steps that need to be completed in sequence in a diagram or list.

For our projects in addition to Java, we will use git and github to host the versions. Before continuing reading, it will be very important that you have trained git and github because Darkness Studio will be talked about a lot!

#GitFlow

GitFlow is a branch organization model in Git that simplifies control of software projects. It establishes a defined structure for the workflow, creating branches for distinct phases of the software lifecycle, such as features, releases, and fixes.

## Branches

- **Main:** Represents the production version of the software.
- **Develop:** This is where active development takes place and all features are integrated.
- **Feature:** Branches to develop new features.
- **Release:** Branches to prepare versions for release.
- **Hotfix:** Branches to fix critical bugs in production.
- **Bugfix:** Branches to fix bugs in branch releases.

## Tag

Tags are labels linked to commits, indicating crucial points in the repository's history. They are generally used to mark software releases, such as release results.

## Step by Step Flow

**Remember to already have a main base branch, such as main, as a development branch will use it as a base. **

### 1. Create or Switch to Branch development

If you already have a Branch developed:

```bash
1. git checkout develop
2. #add some commits if necessary using git add and git commit -m "type(scope): message"
3. git push origin develop
```

If you don't have a Branch developed:

```bash
1. git checkout -b develop
2. #add some commits if necessary using git add and git commit -m "type(scope): message"
3. git push origin develop
```

### 2. Create and Switch to a New Feature Branch:

```bash
1. git checkout -b feature/authenticar-usuario
2. git add authenticar-usuario.js
3. git commit -m "feat: Authenticate User"
4. git push origin/autenticar-usuario feature
```

### 3. Merge Feature Branch and Branch development:
```bash
1. git checkout develop
2. git/autenticar-usuario merge feature
3. git push origin develop
4. git branch -d feature/autenticar-usuario #delete a local branch (optional)
5. git push origin --delete feature/autenticar-usuario #delete a remote branch (optional)
```

### 4. Create and Switch to a New Release Branch;

```bash
1. git checkout -b release/1.0.0
2. git push origin release/1.0.0
```

### 5. Tests must be done on Branch release/1.0.0 (if there is a bug fix);

```bash
1. git checkout release/1.0.0
2. git checkout -b bug fix/timeout error
3. add .
4. git commit -m "fix(bugfix): Fixed timeout error when trying to authenticate user"
5. git push origin bug fix/timeout error
6. git checkout version/1.0.0
7. git merge bug fix/timeout error
8. git push origin release/1.0.0
```

### 6. Merge Release into main and development;

```bash
1. git checkout main
2. git merge release/1.0.0
3. git push main origin

4. git checkout develop
5. git merge release/1.0.0
6. git push origin develop
7. git branch -d release/1.0.0 #delete a local branch (optional)
8. git push origin --delete release/1.0.0 #delete a remote branch (optional)

```

### 7. Create a Tag for the Released Version;

```bash
1. git checkout main
2. git tag -a v1.0.0 -m "Version 1.0.0 - User Authentication Functionality"
3. git push origin v1.0.0

4. git tag
5. git show v1.0.0
```

### 8. Bug Fix in Production: Create and Switch to New Hotfix Branch

```bash
1. git checkout main
2. git checkout -b hotfix/usuario-deactivating
3. add .
4. git commit -m "fix(hotfix): Fix user bug by automatically disabling"
4. git push origin hotfix/user-deactivating
5. git checkout main
6. git merge hotfix/user-deactivating
7. git push main origin
8. git tag -a v1.0.1 -m "Fix bug: User Disabling"
9. git push origin v1.0.1
10. git tag
11.git show v1.0.1
12. git checkout develop
13. git merge hotfix/user-disabling
14. git push origin develop
15. git branch -d hotfix/usuario-deactivating #delete a local branch (optional)
16. git push origin --delete hotfix/user-deactivating #delete a remote branch (optional)
```
