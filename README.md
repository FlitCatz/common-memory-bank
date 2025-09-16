# Common Memory Bank

A collection of integrated memory bank rules for AI development tools. This repository provides memory bank rule files that can be used in various AI development tools such as Cursor, Windsurf, Cline, RooCode, Claude Code etc.
AI 개발 도구를 위한 통합 메모리 뱅크 규칙 모음입니다. 이 리포지토리는 커서, 윈드서프, 클라인, 루코드, 클로드 코드 등 다양한 AI 개발 도구에서 사용할 수 있는 메모리 뱅크 규칙 파일을 제공합니다.

It was specifically written for the purpose of applying memory bank while using **[TaskMaster AI](https://github.com/eyaltoledano/claude-task-master)**.
**[TaskMaster AI](https://github.com/eyaltoledano/claude-task-master)**를 사용하면서 메모리 뱅크를 적용하기 위한 목적으로 특별히 작성되었습니다.

#### Created by [@shalomeir](https://x.com/shalomeir) at [Snippod Inc](https://hello.snippod.com/).

## Overview

Inspired by the [Cline Memory Bank](https://docs.cline.bot/prompting/cline-memory-bank), this project provides a rule file to help maintain context in a consistent way across different AI development tools. 
클라인 메모리 뱅크](https://docs.cline.bot/prompting/cline-memory-bank)에서 영감을 얻은 이 프로젝트는 다양한 AI 개발 도구에서 일관된 방식으로 컨텍스트를 유지하는 데 도움이 되는 규칙 파일을 제공합니다.

In particular, it is designed to allow projects using [TaskMaster AI](https://github.com/eyaltoledano/claude-task-master) to work seamlessly with both the memory bank and `task-master` at the same time.
특히, [태스크마스터 AI](https://github.com/eyaltoledano/claude-task-master)를 사용하는 프로젝트가 메모리 뱅크와 '태스크마스터'를 동시에 원활하게 사용할 수 있도록 설계되었습니다.

## How to use [`common_memory_bank`](./.roo/rules/common_memory_bank.md) rules

### Basic usage

1. Download the rules file or folder for the AI tool you want to use from this repository.
2. Add that file to the rules folder for that tool (`.cursor/rules` or `.roo/rules`)
3. Create a `memory-bank/` folder in your project.
4. Apply the rule files to the AI Agent tool.
5. Follow the guide below to start [Taskmaster](https://github.com/eyaltoledano/claude-task-master).

1. 이 저장소에서 사용하려는 AI 도구의 규칙 파일 또는 폴더를 다운로드합니다.
2. 해당 파일을 해당 도구의 규칙 폴더(`.cursor/rules` 또는 `.roo/rules`)에 추가합니다.
3. 프로젝트에 `memory-bank/` 폴더를 생성합니다.
4. AI 에이전트 도구에 규칙 파일을 적용합니다.
5. 5. 아래 가이드에 따라 [태스크마스터](https://github.com/eyaltoledano/claude-task-master)를 시작합니다.

### Tool-specific application methods

#### Cursor

```bash
mkdir -p YOUR_PROJECT/.cursor/rules && 
cp .cursor/rules/*.* YOUR_PROJECT/.cursor/rules/
```

#### RooCode

```bash
mkdir -p YOUR_PROJECT/.roo/rules && 
cp .roo/rules/*.* YOUR_PROJECT/.roo/rules/
```

#### Cline

```bash
mkdir -p YOUR_PROJECT/.clinerules && 
cp .roo/rules/*.* YOUR_PROJECT/.clinerules/
```

#### Windsurf

```bash
mkdir -p YOUR_PROJECT/.windsurf/rules && 
cp .roo/rules/*.* YOUR_PROJECT/.windsurf/rules/
```



### Using with [TaskMaster AI](https://github.com/eyaltoledano/claude-task-master)

In a project that uses TaskMaster AI, set up as follows

1. Complete the TaskMaster AI setup.
   ```bash
   npm install -g task-master-ai #Install globally
   task-master init
   ```
   > Setting LLM API keys in `.env` for the task-master

2. Initialize the memory bank in the following way.
   - #OPTION1: If you have a previously created PRD (Product Requirements Document), RFP (Request For Proposal) document, etc.
   ```
   Switch to plan mode and initialize the memory-bank based on the attached document.
   ```
    - #OPTION2: Create a project by talking to the agent with the project requirements you want to develop.
   ```
   Let's switch to planning mode and start developing a project. Initialize the memory bank. And let's talk about what kind of project it is. Please reflect it in the memory bank according to the idea. Here are my ideas: {And describe what to make, purpose, target, etc...}
   ```
    - #OPTION3: Create your own based on the form...
   ```
   Switch to plan mode, and fill in the file form for the memory-bank initialization process. A simple example is good to have.
   ```

3. Ask Taskmaster to parse the PRD.
   > First, it asks the agent to create `scripts/prd.txt` based on the memory-bank if it hasn't already been created.

   - OPTION1: Use prompts
   ```
   Please use the task-master parse-prd command to generate tasks from my PRD. The PRD is located at scripts/prd.txt.
   ```
   - OPTION2: `task-master` CLI
   ```bash
   task-master parse-prd scripts/prd.txt
   ```

4. Create a Task file for the Taskmaster.
   - OPTION1: Use prompts
   ```
   Please generate individual task files from tasks.json
   ```
   - OPTION2: `task-master` CLI
   ```bash
   task-master generate
   ```

###  Common prompts
   ```
   Show me the full list of tasks.
   What to do next?
   Switch to ACT MODE, and start Task 3.
   Task 3 is now complete. Please update its status.
   Task 5 seems complex. Can you break it down into subtasks?
   I'd like to implement task 4. Can you help me understand what needs to be done and how to approach it?
   ```

## Additional subrules
We also provide the following subrules files

### [`sub_folder_rules`](./.roo/rules/sub_folder_rules.md)
Folder Path-Based Sub Rule Management System
Rules for creating and managing sub rules within the `.cursor/rules/subrules/` folder.
It creates, manages, and references the context needed during the implementation process within a specific subfolder.
   ```
   Summarize the current work and save it as a subrule.
   ```

### [`preferences`](./.roo/rules/preferences.md)
Prompts for general development quality improvement.
Feel free to modify this to your liking!

### [`role_playing`](./.roo/rules/role_playing.md)
Role-based System: AI assumes AI agents with roles such as Product Manager, Design Engineer, FullStack Developer, Devops Engineer, and QA Engineer.


## Claude Code Commands

When using Claude Code, you can leverage the parallel task execution commands for enhanced development workflows:

### Parallel Worktree Setup
```bash
project:init-parallel <FEATURE_NAME> <NUMBER_OF_WORKTREES>
```
Initializes multiple Git worktrees for parallel development. Creates separate workspace directories for concurrent feature development.

Example:
```bash
project:init-parallel auth-feature 3
```

### Parallel Task Execution
```bash
project:exe-parallel <PLAN_TO_EXECUTE> <NUMBER_OF_PARALLEL_WORKTREES>
```
Executes parallel development tasks across multiple worktrees, enabling concurrent feature implementation and comparison.

These commands utilize the files:
- `.claude/commands/init-parallel.md` - Worktree initialization command
- `.claude/commands/exe-parallel.md` - Parallel execution command


## License
None. Feel free to use it.
