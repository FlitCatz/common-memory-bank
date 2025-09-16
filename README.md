# Common Memory Bank

[Cline site 원본](https://docs.cline.bot/prompting/cline-memory-bank)

AI 개발 도구를 위한 통합 Memory Bank 규칙 모음입니다. 이 Repository 는 Cursor, Windsurf, Cline, RooCode, Claude Code 등 다양한 AI 개발 도구에서 사용할 수 있는 Memory Bank 규칙 파일을 제공합니다.

**[TaskMaster AI](https://github.com/eyaltoledano/claude-task-master)** 를 사용하면서 Memory Bank 를 적용하기 위한 목적으로 특별히 작성되었습니다.

#### Created by [@shalomeir](https://x.com/shalomeir) at [Snippod Inc](https://hello.snippod.com/).

## Overview

[Cline Memory Bank](https://docs.cline.bot/prompting/cline-memory-bank) 에서 영감을 얻은 이 프로젝트는 다양한 AI 개발 도구에서 일관된 방식으로 컨텍스트를 유지하는 데 도움이 되는 규칙 파일을 제공합니다.

특히, [TaskMaster AI](https://github.com/eyaltoledano/claude-task-master) 를 사용하는 프로젝트가 Memory Bank와 TaskMaster 를 동시에 원활하게 사용할 수 있도록 설계되었습니다.

## How to use [`common_memory_bank`](./.cursor/rules/common_memory_bank.md) rules

### Basic usage

1. 이 저장소에서 사용하려는 AI 도구의 규칙 파일 또는 폴더를 다운로드합니다.
2. 해당 파일을 해당 도구의 규칙 폴더(`.cursor/rules` 또는 `.roo/rules`)에 추가합니다.
3. 프로젝트에 `memory-bank/` 폴더를 생성합니다.
4. AI 에이전트 도구에 규칙 파일을 적용합니다.
5. 아래 가이드에 따라 [TaskMaster AI](https://github.com/eyaltoledano/claude-task-master)를 시작합니다.

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

TaskMaster AI를 사용하는 프로젝트에서는 다음과 같이 설정합니다.

1. TaskMaster AI 설치를 완료합니다.
   ```bash
   npm install -g task-master-ai #Install globally
   task-master init
   ```
   > task-master에 대해 '.env'에 LLM API 키 설정

2. 다음과 같은 방법으로 Memory Bank 를 초기화합니다.

   - #OPTION 1: 이전에 생성한 PRD(제품 요구사항 문서), RFP(제안요청서) 문서 등이 있는 경우.
   ```
   계획 모드로 전환하고 첨부된 문서를 기반으로 메모리 뱅크를 초기화합니다.
   ```
   - #OPTION 2: 개발하고자 하는 프로젝트 요구사항을 Agent와 대화하여 프로젝트를 생성합니다.
   ```
   계획 모드로 전환하여 프로젝트 개발을 시작하겠습니다.
   메모리 뱅크를 초기화합니다. 그리고 어떤 종류의 프로젝트인지 이야기해 봅시다.
   아이디어에 따라 메모리 뱅크에 반영해 주세요.
   제 아이디어는 다음과 같습니다: {그리고 무엇을 만들 것인지, 목적, 대상 등을 설명하세요...}
   ```
   - #OPTION 3: 양식에 따라 직접 작성...
   ```
   계획 모드로 전환하고 메모리뱅크 초기화 프로세스를 위한 파일 양식을 작성합니다. 간단한 예제가 있으면 좋습니다.
   ```

3. 태스크마스터에게 PRD를 파싱하도록 요청합니다.
   > 먼저 아직 만들어지지 않은 경우 Memory Bank에 따라 `scripts/prd.txt`를 만들도록 에이전트에게 요청합니다.
   
   - OPTION 1: 프롬프트 사용
   ```
   내 PRD에서 작업을 생성하려면 task-master parse-prd 명령을 사용하세요. PRD는 스크립트/prd.txt에 있습니다.
   ```
   - OPTION 2: `task-master` CLI
   ```bash
   task-master parse-prd scripts/prd.txt
   ```

4. 작업 마스터를 위한 작업 파일을 만듭니다.

   - 옵션1: 프롬프트 사용
   ```
   tasks.json에서 개별 작업 파일을 생성하세요.
   ```
   - 옵션2: `task-master` CLI
   ```bash
   task-master generate
   ```

###  Common prompts
   ```
   전체 작업 목록을 표시합니다.
   다음에 무엇을 할까요?
   작업 모드로 전환하고 작업 3을 시작합니다.
   이제 작업 3이 완료되었습니다. 상태를 업데이트하세요.
   작업 5가 복잡해 보입니다. 하위 작업으로 나눌 수 있나요?
   작업 4를 구현하고 싶습니다. 어떤 작업을 수행해야 하고 어떻게 접근해야 하는지 알려주실 수 있나요?
   ```

## Additional subrules
또한 다음과 같은 하위 규칙 파일도 제공합니다.

### [`sub_folder_rules`](./.roo/rules/sub_folder_rules.md)
폴더 경로 기반 하위 규칙 관리 시스템
`.cursor/rules/subrules/` 폴더 내에서 하위 규칙을 생성하고 관리하기 위한 규칙으로, 특정 하위 폴더 내에서 구현 과정에서 필요한 컨텍스트를 생성, 관리, 참조할 수 있습니다.
```
⁠현재 작업을 요약하여 하위 규칙으로 저장합니다.
```
### [`preferences`](./.roo/rules/preferences.md)
일반적인 개발 품질 향상을 위한 프롬프트입니다.
원하는 대로 자유롭게 수정하세요!

### [`role_playing`](./.roo/rules/role_playing.md)
역할 기반 시스템: AI는 제품 관리자, 디자인 엔지니어, 풀스택 개발자, 개발 엔지니어, QA 엔지니어와 같은 역할을 가진 AI 에이전트를 가정합니다.

## Claude Code Commands

클로드 코드를 사용하면 병렬 작업 실행 명령을 활용하여 개발 워크플로우를 개선할 수 있습니다:

### Parallel Worktree Setup
```bash
project:init-parallel <FEATURE_NAME> <NUMBER_OF_WORKTREES>
```
병렬 개발을 위해 여러 Git 워크트리를 초기화합니다. 동시 기능 개발을 위해 별도의 작업 공간 디렉터리를 만듭니다.

Example:
```bash
project:init-parallel auth-feature 3
```

### Parallel Task Execution
```bash
project:exe-parallel <PLAN_TO_EXECUTE> <NUMBER_OF_PARALLEL_WORKTREES>
```
여러 워크트리에서 병렬 개발 작업을 실행하여 동시에 기능을 구현하고 비교할 수 있습니다.

These commands utilize the files:
- `.claude/commands/init-parallel.md` - Worktree initialization command
- `.claude/commands/exe-parallel.md` - Parallel execution command

## License
없음. 자유롭게 사용하세요.
