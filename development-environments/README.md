# Integrated Development Environments (IDEs)

## 1. What Is an IDE?

An **Integrated Development Environment (IDE)** is a software application that combines the tools a programmer needs in a single interface.

### Typical IDE components

| Component | Purpose |
|-----------|---------|
| Code editor | Syntax highlighting, auto-completion, formatting |
| Compiler / interpreter integration | Build and run code with one click |
| Debugger | Pause execution, step through code, inspect variables |
| Project explorer | Browse files and folders |
| Refactoring tools | Safely rename or restructure code |
| Version control integration | Commit, branch, and merge without leaving the IDE |
| Plugins / extensions | Add languages, frameworks, and tools |

### Why IDEs matter

- **Productivity**: auto-completion and code generation save time.
- **Fewer errors**: real-time error detection highlights mistakes as you type.
- **Easier debugging**: breakpoints and variable inspection beat print statements.
- **Consistency**: the whole team can share project settings.
- **Integration**: testing, building, and Git are in one place.

### IDE vs text editor

A text editor (Notepad, Vim) edits text. An IDE understands your project: it knows your classes, finds usages, and runs tests. Editors such as **VS Code** sit in between: lightweight, but extensible to IDE-like behaviour.

---

## 2. Popular IDEs

### Eclipse

- **Platform:** Windows, macOS, Linux.
- **Languages:** Java primarily; C/C++, PHP, and others through plugins.
- **Cost:** Free and open source.
- **Strengths:** Huge plugin ecosystem; common in universities and enterprise Java.
- **Limitations:** Interface can feel dated; heavy plugin setups can be slow.
- **Website:** https://www.eclipse.org/downloads/

### IntelliJ IDEA

- **Platform:** Windows, macOS, Linux.
- **Languages:** Java and Kotlin primarily; others via plugins or sibling JetBrains IDEs.
- **Cost:** Community Edition is free; Ultimate is paid (free for students through JetBrains' education programme).
- **Strengths:** Excellent code analysis, refactoring, and suggestions.
- **Limitations:** Uses more memory; some advanced features only in Ultimate.
- **Website:** https://www.jetbrains.com/idea/

### NetBeans

- **Platform:** Windows, macOS, Linux.
- **Languages:** Java, PHP, JavaScript, HTML5, C/C++.
- **Cost:** Free and open source (Apache project).
- **Strengths:** Simple to start with; good built-in GUI designer for Java Swing; Maven and Git support.
- **Limitations:** Smaller plugin ecosystem than Eclipse or IntelliJ.
- **Website:** https://netbeans.apache.org

### Microsoft Visual Studio

- **Platform:** Windows (a separate Visual Studio Code editor runs on all platforms).
- **Languages:** C#, C++, VB.NET, F#, Python, JavaScript/TypeScript.
- **Cost:** Community Edition is free for students, individuals, and small teams; Professional and Enterprise are paid.
- **Strengths:** Top-tier debugger; best choice for .NET and Windows development; built-in Git and Azure DevOps integration.
- **Limitations:** Large installation; full IDE is Windows-only.
- **Website:** https://visualstudio.microsoft.com

### Xcode

- **Platform:** macOS only.
- **Languages:** Swift, Objective-C, C/C++.
- **Cost:** Free from the Mac App Store.
- **Strengths:** Official tool for building iOS, iPadOS, macOS, watchOS, and tvOS apps; includes simulators and Interface Builder.
- **Limitations:** Requires a Mac; focused on Apple platforms.
- **Website:** https://developer.apple.com/xcode/

### Comparison

| IDE | OS | Main languages | Cost | Typical use |
|-----|----|----------------|------|-------------|
| Eclipse | Win / Mac / Linux | Java | Free | Enterprise Java, teaching |
| IntelliJ IDEA | Win / Mac / Linux | Java, Kotlin | Free Community / paid Ultimate | Professional Java and Kotlin |
| NetBeans | Win / Mac / Linux | Java, PHP | Free | Learning Java, desktop apps |
| Visual Studio | Windows | C#, C++ | Free Community / paid | .NET and Windows apps |
| Xcode | macOS | Swift | Free | Apple platform apps |

### How to choose

1. **Language and platform** come first (Swift means Xcode; C#/.NET means Visual Studio).
2. **Course requirements**: use what your instructor specifies.
3. **Computer resources**: older machines may prefer a lighter editor.
4. **Team consistency**: agree on one setup where possible.

---

## 3. Browser-Based Alternatives

If you cannot install software (shared lab, Chromebook, tablet), cloud-based environments run in a web browser.

| Tool | Description |
|------|-------------|
| **GitHub Codespaces** | A full VS Code environment in the browser, attached to a GitHub repository. Free monthly usage allowance for personal accounts. |
| **github.dev** | A lightweight editor: press `.` on any GitHub repository page. Good for editing files and committing, but cannot run code. |
| **Replit** | Browser IDE supporting many languages with instant run and sharing. |
| **StackBlitz** | Browser IDE focused on web development (JavaScript, Node.js). |
| **Gitpod** | Cloud development environments linked to Git repositories. |

### Advantages

- No installation; start in seconds.
- Same environment for everyone on the team.
- Works on any device with a browser.

### Disadvantages

- Requires a stable internet connection.
- Free usage has limits.
- Less customisation and sometimes lower performance than a local IDE.

### Try it: GitHub Codespaces

1. Open your repository on GitHub.
2. Click the green **Code** button, then the **Codespaces** tab.
3. Click **Create codespace on main**.
4. Edit a file, then use the **Source Control** panel to commit and push.

---

## 4. Using Git Inside an IDE

Most IDEs include Git tools. Common actions:

| Action | Typical location |
|--------|------------------|
| Clone a repository | *File > Open from Version Control* (IntelliJ), *File > Import > Git* (Eclipse), *Team > Git* (NetBeans), *Clone a repository* start screen (Visual Studio), *Source Control* menu (Xcode) |
| Stage and commit | Commit or Source Control panel |
| Create a branch | Branch selector in the status bar or Git menu |
| Push and pull | Git or Team menu |

Learning the command line first (see [git-and-github](../git-and-github/basic-git-commands.md)) makes the IDE buttons easier to understand.

---

## Key Points

- An IDE combines an editor, build tools, debugger, and version control in one application.
- Choose an IDE based on language, platform, and course needs.
- Browser-based environments such as Codespaces and Replit remove installation barriers.

## References

- Eclipse: https://www.eclipse.org
- IntelliJ IDEA documentation: https://www.jetbrains.com/help/idea/
- NetBeans: https://netbeans.apache.org
- Visual Studio documentation: https://learn.microsoft.com/visualstudio/
- Xcode documentation: https://developer.apple.com/documentation/xcode
- GitHub Codespaces documentation: https://docs.github.com/en/codespaces
- Replit documentation: https://docs.replit.com
