# AI CLI Project - Agent Guidelines

## Project Overview
This is a technical knowledge base for AI development experience, including AI agent development, RAG systems, AI plugins, and various tool implementations. The main web application is built with Vue 3 + Vite.

## Build/Test Commands

### Main Commands
```bash
# Development
npm run dev                    # Start development server

# Build & Production
npm run build                  # Build for production
npm run preview                # Preview production build

# Code Quality
npm run lint                   # Run ESLint (auto-fix)
npm run format                 # Run Prettier formatting

# Testing
npm run test                   # Run all tests
npm run test:coverage          # Run tests with coverage report
```

### Running a Single Test
```bash
# Run specific test file
npx vitest path/to/test.spec.js

# Run tests matching pattern
npx vitest --run ToolCard

# Watch mode for specific test
npx vitest ToolCard.spec.js
```

### Web App (ai_tools/ai-tools/website)
The web application uses the same commands but run in the `website` directory.

## Code Style Guidelines

### Formatting & Linting
- **Indentation**: 2 spaces for JS/TS/Vue, 4 spaces for Python
- **Line Ending**: LF only (no CRLF)
- **Character Encoding**: UTF-8
- **Semicolons**: No semicolons (Prettier: `"semi": false`)
- **Quotes**: Single quotes (`"singleQuote": true`)
- **Trailing Commas**: None (`"trailingComma": "none"`)
- **Line Width**: 100 characters (`"printWidth": 100`)
- **Final Newline**: Required

### Imports
```javascript
// Vue Composition API
import { ref, computed, onMounted } from 'vue'
import { useRouter } from 'vue-router'

// Components
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'

// Utilities
import { formatDate, debounce } from './utils/helpers.js'

// Icons (lucide-vue-next)
import { CheckCircle, AlertCircle } from 'lucide-vue-next'
```

### Vue Components
```vue
<script setup>
// Always use Composition API with <script setup>
import { ref, computed, onMounted } from 'vue'

// Props definition
defineProps({
  tool: {
    type: Object,
    required: true
  }
})

// Use Pinia for state management
import { useStore } from '@/stores/store'
const store = useStore()
</script>
```

### Naming Conventions
- **Components**: PascalCase (e.g., `ToolCard.vue`, `ErrorBoundary.vue`)
- **Files**: kebab-case (e.g., `tool-detail.vue`, `use-performance.js`)
- **Functions**: camelCase (e.g., `formatDate`, `getRatingStars`)
- **Constants**: UPPER_SNAKE_CASE (e.g., `MAX_RETRY_COUNT`)
- **CSS Classes**: Tailwind utility classes preferred
- **Directories**: lowercase with hyphens (e.g., `ai-tools`, `composables`)

### Error Handling
```javascript
// Try-catch with proper error messages
try {
  const result = await fetchData()
} catch (error) {
  console.error('Failed to fetch data:', error)
  // Show user-friendly error message
  showError('数据加载失败，请稍后重试')
}

// Use ErrorBoundary component for Vue errors
<ErrorBoundary>
  <YourComponent />
</ErrorBoundary>
```

### Testing (Vitest)
```javascript
// Test file naming: *.spec.js in __tests__ directory
import { describe, it, expect } from 'vitest'
import { mount } from '@vue/test-utils'

describe('ToolCard', () => {
  it('renders tool name', () => {
    const wrapper = mount(ToolCard, { props: { tool } })
    expect(wrapper.text()).toContain('Expected Text')
  })
})
```

### File Organization
```
src/
├── components/        # Reusable Vue components
├── views/            # Page-level components
├── composables/      # Vue composition functions
├── stores/           # Pinia state management
├── utils/            # Helper functions
├── router/           # Vue Router config
├── data/             # Static data files
└── main.js           # Entry point
```

### Documentation
- Use Chinese for user-facing content
- Use English for code comments and technical documentation
- Include JSDoc comments for complex functions
- Keep README.md files up-to-date

### Git Workflow
- Branch naming: `feature/description` or `fix/description`
- Commit messages: `Type: Description` (e.g., `Add: Component name`, `Fix: Bug description`)
- Follow the CONTRIBUTING.md guidelines for file naming and content structure

### Performance
- Use `defineAsyncComponent` for route-level code splitting
- Lazy load non-critical components
- Use `v-show` instead of `v-if` for frequently toggled content
- Implement proper loading states with LoadingSpinner component

### Security
- Sanitize user inputs
- Use `rel="noopener noreferrer"` for external links
- Keep dependencies updated
- Follow security best practices for API keys and sensitive data

## Quick Reference
- **ESLint Config**: `.eslintrc.cjs` (Vue3 recommended, no unused vars warning)
- **Prettier Config**: `.prettierrc` (no semicolons, single quotes)
- **EditorConfig**: `.editorconfig` (enforces consistent editor settings)
- **Test Framework**: Vitest with Vue Test Utils
- **Styling**: Tailwind CSS v3.4

## Important Notes
- All documentation should be in Chinese as per project requirements
- Follow `.editorconfig` for cross-editor consistency
- Run `npm run lint` and `npm run format` before committing
- Tests are located in `__tests__` subdirectories
- Use Pinia for state management instead of Vuex
