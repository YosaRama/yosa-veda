# Checklist

### 🧠 1. Core Mental Models (FOUNDATION)

You should be able to explain **without framework terms**:

* [ ] What is **rendering** vs **hydration**
* [ ] Difference between **state**, **props**, **derived state**
* [ ] Push vs pull reactivity
* [ ] Why immutability matters (and when it doesn’t)
* [ ] Declarative UI vs imperative DOM
* [ ] Controlled vs uncontrolled components

👉 If you can teach this, frameworks become easy.

***

### 🧩 2. Rendering & Architecture Models

You should confidently design apps using:

* [ ] CSR (Client-Side Rendering)
* [ ] SSR (Server-Side Rendering)
* [ ] SSG (Static Generation)
* [ ] Streaming SSR
* [ ] Partial hydration
* [ ] Islands architecture
* [ ] Client-only vs server-only logic

You should be able to answer:

> Where does this code run?\
> When does it execute?\
> Why here?

***

### 🌐 3. Browser Internals (HUGE separator)

You understand how browsers actually work:

* [ ] Event loop
* [ ] Microtasks vs macrotasks
* [ ] Call stack
* [ ] Reflow vs repaint
* [ ] Layout thrashing
* [ ] requestAnimationFrame
* [ ] Compositing layers
* [ ] Garbage collection basics

👉 This explains 80% of “weird frontend bugs”.

***

### 🔄 4. Data & Networking

You design data flow intentionally:

* [ ] REST vs GraphQL tradeoffs
* [ ] HTTP caching (Cache-Control, ETag)
* [ ] CDN behavior
* [ ] Request waterfalls
* [ ] Optimistic UI
* [ ] Server state vs client state
* [ ] Stale-while-revalidate

You understand:

> UI is a projection of remote state.

***

### 🧠 5. State Architecture (NOT libraries)

You can reason about:

* [ ] Local vs global state
* [ ] Server state vs UI state
* [ ] Derived vs source state
* [ ] Ephemeral vs persistent state
* [ ] Ownership of state
* [ ] State colocated vs centralized

You can explain _why_ a state lives where it lives.

***

### ⚡ 6. Performance as Architecture

You think about performance **before** code:

* [ ] Critical rendering path
* [ ] Bundle splitting strategies
* [ ] Tree shaking
* [ ] Lazy loading routes/components
* [ ] Memory profiling
* [ ] Web Vitals (LCP, CLS, INP)
* [ ] Perceived performance techniques

You know:

> Performance problems are usually design problems.

***

### ♿ 7. Accessibility (Often ignored, very senior)

You can build accessible UI by default:

* [ ] Semantic HTML
* [ ] Keyboard navigation
* [ ] Focus management
* [ ] Screen reader basics
* [ ] ARIA (when needed, not always)
* [ ] Reduced motion preferences
* [ ] Color contrast

Frameworks don’t solve this — you do.

***

### 🎨 8. CSS as a First-Class Skill

You understand layout & styling deeply:

* [ ] Flexbox vs Grid (when & why)
* [ ] Stacking contexts
* [ ] Containing blocks
* [ ] CSS variables & tokens
* [ ] Modern selectors (`:has`, `:where`)
* [ ] Responsive design principles
* [ ] Avoiding layout hacks

Great CSS = simpler JS.

***

### 🧱 9. Component & UI Architecture

You can design systems that scale:

* [ ] Component boundaries
* [ ] Composition over inheritance
* [ ] Headless components
* [ ] Controlled vs uncontrolled components
* [ ] Slot / render prop patterns
* [ ] Design tokens
* [ ] Theming strategies

This is where large apps succeed or fail.

***

### 🔐 10. Frontend Security (Practical)

You understand real risks:

* [ ] XSS (how it actually happens)
* [ ] CSRF
* [ ] CORS
* [ ] Cookie flags (HttpOnly, SameSite)
* [ ] Token storage tradeoffs
* [ ] Clickjacking
* [ ] Trust boundaries

Security is about **data flow**, not libraries.

***

### 🧪 11. Testing as Confidence

You test with intention:

* [ ] Testing pyramid
* [ ] What NOT to test
* [ ] Component testing vs integration
* [ ] Visual regression
* [ ] Contract testing
* [ ] Mocking strategies

Tests answer:

> “Can I change this safely?”

***

### 🛠️ 12. DX & Maintainability

You care about team velocity:

* [ ] Build performance
* [ ] CI feedback loops
* [ ] Error boundaries
* [ ] Logging & observability
* [ ] Feature flags
* [ ] Progressive rollout

Senior engineers optimize **people**, not just code.

***

### 🧠 13. Product & UX Thinking (Hidden multiplier)

You think beyond UI correctness:

* [ ] Loading states psychology
* [ ] Empty states
* [ ] Error states
* [ ] Progressive disclosure
* [ ] User intent vs system state
* [ ] Accessibility as UX

Frontend is closest to users — this matters.
