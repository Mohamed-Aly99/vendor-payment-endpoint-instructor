
````md
# Installing `vendor-payment-endpoint-instructor` for OpenCode

## Prerequisites

- [OpenCode](https://opencode.ai) installed
- The full skill files available locally:
  - `SKILL.md`
  - `references/explanation-contract.md`
  - `references/repo-scope.md`
  - `references/validation-scenarios.md`

## What this is

This is an OpenCode **skill**, not a plugin.

That means you install it by placing a folder named `vendor-payment-endpoint-instructor` in one of OpenCode’s supported `skills` directories, with `SKILL.md` inside that folder.

## Required folder structure

Your installed files should look like this:

```text
vendor-payment-endpoint-instructor/
├── SKILL.md
└── references/
    ├── explanation-contract.md
    ├── repo-scope.md
    └── validation-scenarios.md
````

Important:

- The folder name must be exactly `vendor-payment-endpoint-instructor`
    
- The `name` in the skill frontmatter must match that folder name
    
- `SKILL.md` must stay uppercase and remain at the root of the skill folder
    
- Keep the `references/` directory, because the skill instructions point to those files
    

## Install options

### Option 1: Install for one project only

Copy the skill into your project at:

```text
.opencode/skills/vendor-payment-endpoint-instructor/
```

Result:

```text
your-project/
└── .opencode/
    └── skills/
        └── vendor-payment-endpoint-instructor/
            ├── SKILL.md
            └── references/
                ├── explanation-contract.md
                ├── repo-scope.md
                └── validation-scenarios.md
```

### Option 2: Install globally for all projects

Copy the skill into:

```text
~/.config/opencode/skills/vendor-payment-endpoint-instructor/
```

Result:

```text
~/.config/opencode/
└── skills/
    └── vendor-payment-endpoint-instructor/
        ├── SKILL.md
        └── references/
            ├── explanation-contract.md
            ├── repo-scope.md
            └── validation-scenarios.md
```

## Example install commands

### Project-level install

Run these commands from the directory that contains `SKILL.md` and the `references/` folder:

```bash
mkdir -p .opencode/skills/vendor-payment-endpoint-instructor/references
cp SKILL.md .opencode/skills/vendor-payment-endpoint-instructor/SKILL.md
cp references/explanation-contract.md .opencode/skills/vendor-payment-endpoint-instructor/references/
cp references/repo-scope.md .opencode/skills/vendor-payment-endpoint-instructor/references/
cp references/validation-scenarios.md .opencode/skills/vendor-payment-endpoint-instructor/references/
```

### Global install

```bash
mkdir -p ~/.config/opencode/skills/vendor-payment-endpoint-instructor/references
cp SKILL.md ~/.config/opencode/skills/vendor-payment-endpoint-instructor/SKILL.md
cp references/explanation-contract.md ~/.config/opencode/skills/vendor-payment-endpoint-instructor/references/
cp references/repo-scope.md ~/.config/opencode/skills/vendor-payment-endpoint-instructor/references/
cp references/validation-scenarios.md ~/.config/opencode/skills/vendor-payment-endpoint-instructor/references/
```

## Verify installation

Start OpenCode in the target project and try one of these:

```text
use skill tool to list skills
```

Then:

```text
use skill tool to load vendor-payment-endpoint-instructor
```

Or ask OpenCode with a prompt that should trigger the skill, for example:

```text
Use vendor-payment-endpoint-instructor to explain POST /api/auth/login in staged mode.
```

## What this skill is for

This skill is designed to explain **one backend endpoint** from:

- `vendor_payment_system`
    
- `vendor_payment_system.shared`
    

It is intended for exhaustive, beginner-friendly endpoint walkthroughs, especially when the user asks for every step, every detail, or asks not to summarize.

## Usage examples

```text
Use vendor-payment-endpoint-instructor to explain POST /api/auth/login in staged mode.
```

```text
Use vendor-payment-endpoint-instructor to explain the Create-Respond endpoint.
```

```text
Use vendor-payment-endpoint-instructor to explain POST /api/users in full mode.
```

## Notes

- No `plugin` entry is required in `opencode.json` for this skill
    
- You do not need to convert this into JavaScript or TypeScript
    
- Install the entire folder, not `SKILL.md` alone
    
- Project-level installation is best when the skill belongs to a single repository
    
- Global installation is best when you want the skill available everywhere
    

## Troubleshooting

### Skill does not appear

1. Confirm the path is one of OpenCode’s supported skill paths
    
2. Confirm the folder name is exactly `vendor-payment-endpoint-instructor`
    
3. Confirm `SKILL.md` is named exactly `SKILL.md`
    
4. Confirm the frontmatter in `SKILL.md` includes:
    
    - `name: vendor-payment-endpoint-instructor`
        
    - `description: ...`
        
5. Confirm the `references/` files were copied too
    
6. Check whether skill permissions are denying access
    

### Skill loads but behaves oddly

1. Make sure the skill is being used inside the correct repository
    
2. Make sure the backend paths referenced by the skill actually exist in the repo
    
3. Try the validation prompts from `references/validation-scenarios.md`
    
4. Avoid asking it about frontend pages, because this skill is backend-only
    

## Updating

Replace the installed files with the newer versions of:

- `SKILL.md`
    
- `references/explanation-contract.md`
    
- `references/repo-scope.md`
    
- `references/validation-scenarios.md`
    

## Uninstalling

Remove the installed skill folder.

### Remove project-level install

```bash
rm -rf .opencode/skills/vendor-payment-endpoint-instructor
```

### Remove global install

```bash
rm -rf ~/.config/opencode/skills/vendor-payment-endpoint-instructor
```
