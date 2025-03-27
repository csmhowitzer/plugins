# Refactor.nvim

A Neovim plugin for code refactoring operations, with initial support for Lua and C#.

## Features (Planned)

- Extract selected code block into a new function
- Smart function name suggestions based on code context
- Language-specific refactoring rules
- Initial language support:
  - Lua
  - C#

## Requirements

- Neovim >= 0.8.0
- treesitter (for syntax awareness)

## Installation

Using [lazy.nvim](https://github.com/folke/lazy.nvim):

```lua
{
    "yourusername/Refactor.nvim",
    dependencies = {
        "nvim-treesitter/nvim-treesitter",
    },
    config = function()
        require("refactor").setup()
    end
}
```
## Usage

Default keymaps (can be customized):
- Visual mode: `<leader>re` - Extract selected code into a new function

## Development Notes

### Extract Function Feature

1. Core Functionality:
   - Capture selected text in visual mode
   - Analyze code context using treesitter
   - Determine scope and required parameters
   - Generate function signature
   - Replace original code with function call
   - Insert new function definition in appropriate location

2. Language-specific Handlers:
   - Lua implementation
   - C# implementation
   - Extensible architecture for adding more languages

3. Technical Considerations:
   - Parameter detection
   - Return value handling
   - Scope analysis
   - Variable declaration handling
   - Maintaining proper indentation
   - Handling comments

4. Future Enhancements:
   - Automatic function naming based on code content
   - Multiple return value support
   - Refactoring preview
   - Undo/redo support
   - Additional refactoring operations (Extract method, Extract class, etc.)

### Project Structure

```
Refactor.nvim/
├── lua/
│   └── refactor/
│       ├── init.lua
│       ├── config.lua
│       ├── extract.lua
│       └── langs/
│           ├── lua.lua
│           └── csharp.lua
├── README.md
└── LICENSE
```

### Implementation Plan

1. Phase 1: Basic Infrastructure
   - Set up project structure
   - Implement configuration handling
   - Add visual selection utilities
   - Create basic extraction logic

2. Phase 2: Lua Support
   - Implement Lua-specific extraction rules
   - Handle variable scope
   - Generate function signatures
   - Manage return values

3. Phase 3: C# Support
   - Implement C# extraction rules
   - Handle access modifiers
   - Manage type declarations
   - Support method overloading

4. Phase 4: Enhancements
   - Add function name suggestions
   - Implement refactoring preview
   - Add additional refactoring operations
   - Improve error handling and user feedback

# Development Notes

## Initial Research

### Key Components Needed

1. **Selection Handling**
   - Need to capture visual mode selection
   - Get start and end positions
   - Handle multi-line selections
   - Preserve indentation

2. **AST Analysis**
   - Use treesitter for parsing
   - Identify variables and their scope
   - Detect dependencies
   - Handle nested structures

3. **Code Generation**
   - Create function signatures
   - Generate parameter list
   - Handle return values
   - Maintain code style

### Similar Projects to Study

1. **vim-refactor**: Basic refactoring operations
2. **refactoring.nvim**: More complex refactoring tools
3. **lua-refactor**: Lua-specific refactoring

## Implementation Details

### Phase 1: Basic Infrastructure

```lua
-- Example structure for extract.lua
local M = {}

M.extract_function = function(opts)
    -- 1. Get visual selection
    -- 2. Analyze code context
    -- 3. Generate function
    -- 4. Replace original code
    -- 5. Insert new function
end

return M
```

### Language-specific Considerations

#### Lua
- No type declarations needed
- Multiple return values supported
- Global/local scope considerations
- No class structure to worry about

#### C#
- Need to handle access modifiers
- Type declarations required
- Class context important
- Single return value (but can use tuple)

## TODO

- [ ] Set up basic plugin structure
- [ ] Implement visual selection handling
- [ ] Add treesitter integration
- [ ] Create basic Lua extractor
- [ ] Add C# support
- [ ] Implement configuration system
- [ ] Add tests
- [ ] Create documentation

## References

- Neovim API documentation
- Treesitter documentation
- Language specifications for Lua and C#
- Existing refactoring tools and patterns
