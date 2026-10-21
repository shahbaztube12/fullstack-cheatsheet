# 📚 Full Stack Cheat Sheet

> Every term I use as a Frontend Engineer — explained clearly.  
> One-liner + follow-up answer for every concept.  
> **30 terms** across Frontend, Backend, Database, Tooling & Certifications.

🌐 **Live site:** [shahbaztube12.github.io/cheatsheet](https://shahbaztube12.github.io/cheatsheet)  
👨‍💻 **Author:** [Mohd Shahbaz](https://github.com/shahbaztube12) — Frontend Engineer · React · Next.js · Node.js

---

## 📑 Table of Contents

- [Frontend](#-frontend)
- [Backend](#-backend)
- [Database](#-database)
- [Tooling & DevOps](#-tooling--devops)
- [Certifications](#-certifications)

---

## 🟣 Frontend

### Axios
**One-liner:** HTTP client library for making API calls in JavaScript — simpler syntax than fetch, with built-in JSON parsing and error handling.

**If follow-up asked:**
> Interceptors ek middleware ki tarah kaam karte hain — har request ya response ke beech mein code run karte hain. Jaise: har request mein Authorization header auto-add karo, ya 401 error pe auto logout karo.

```js
axios.interceptors.request.use(config => {
  config.headers.Authorization = `Bearer ${token}`;
  return config;
});
```

---

### React Hooks
**One-liner:** Functions jo functional components mein state aur lifecycle features use karne dete hain — useState, useEffect, useMemo, useCallback, useRef.

**If follow-up asked:**
> - `useState` → state manage karna  
> - `useEffect` → API calls, subscriptions (side effects)  
> - `useMemo` → expensive computation memoize karna  
> - `useCallback` → function reference stable rakhna  
> - `useRef` → DOM element access ya mutable value

---

### useMemo vs useCallback
**One-liner:** `useMemo` ek computed value memoize karta hai. `useCallback` ek function ka reference memoize karta hai taaki unnecessary re-renders na hon.

```js
const filtered = useMemo(() => items.filter(i => i.active), [items]);
const handleDelete = useCallback((id) => remove(id), [remove]);
```

---

### Virtual DOM & Reconciliation
**One-liner:** React pehle ek virtual (in-memory) copy of DOM banata hai, changes compare karta hai real DOM se, aur sirf jo parts change hue unhe update karta hai — ye reconciliation hai.

**If follow-up asked:**
> Kyun fast hai: Full page refresh nahi hoti. React sirf diff (difference) calculate karta hai aur minimum DOM operations run karta hai. Ye algorithm "diffing" kehlaata hai.

---

### SSR — Server Side Rendering
**One-liner:** Page ka HTML server pe render hota hai aur complete page browser ko milta hai — SEO aur first load ke liye fast, especially marketing pages ke liye.

```js
// Next.js App Router — server component by default
async function Page() {
  const data = await fetch('/api/data'); // server pe run hoga
  return <div>{data}</div>;
}
```

---

### SSG — Static Site Generation
**One-liner:** Build time pe HTML generate hota hai — har request pe server nahi lagta, CDN se serve hota hai — blog, landing pages ke liye best.

**If follow-up asked:**
> Next.js mein `generateStaticParams` ya static export. Fast, cheap, SEO-friendly. Sirf jab content frequently change nahi karta tab use karo.

---

### ISR — Incremental Static Regeneration
**One-liner:** SSG + auto-update — page build time pe banta hai but background mein X seconds baad automatically regenerate hota hai.

```js
export const revalidate = 60; // 60 seconds baad regenerate
async function Page() {
  const product = await getProduct();
  return <ProductPage product={product} />;
}
```

---

### Next.js App Router
**One-liner:** Next.js 13+ ka naya routing system — file-based routing, Server Components by default, layouts, streaming sab built-in.

**If follow-up asked:**
> Pages Router se difference: App Router mein `app/` folder use karte hain, components by default server-side hain, `'use client'` likho tab hi browser pe chalte hain.

---

### Tailwind CSS
**One-liner:** Utility-first CSS framework — predefined classes seedha HTML mein likhte hain, custom CSS bahut kam likhna padta hai.

```jsx
<div className="flex items-center gap-4 p-6 rounded-xl bg-white shadow-sm">
  <span className="text-sm font-medium text-gray-900">Card</span>
</div>
```

---

### shadcn/ui
**One-liner:** Ready-made accessible React components (Radix UI pe based) — copy-paste karo apne project mein, customize karo — npm install nahi hota.

```bash
npx shadcn-ui@latest add button dialog
```

**If follow-up asked:**
> Radix UI se difference: Radix headless (unstyled) components deta hai, shadcn unke upar Tailwind styling add karta hai. shadcn mein full ownership hota hai code ka.

---

### Radix UI
**One-liner:** Headless (unstyled) accessible React component primitives — Dialog, Dropdown, Tooltip etc. — accessibility built-in, styling khud karo.

**If follow-up asked:**
> WCAG accessibility standards automatically follow hoti hain, keyboard navigation aur screen reader support free mein milti hai. shadcn/ui Radix ke upar hi bana hai.

---

### Redux
**One-liner:** Global state management library — jab multiple components ko ek hi data share karna ho aur prop-drilling se bachna ho tab use karta hai.

```js
const counterSlice = createSlice({
  name: 'counter',
  initialState: { value: 0 },
  reducers: { increment: state => { state.value++ } }
});
dispatch(increment());
```

---

### Context API
**One-liner:** React ka built-in state sharing mechanism — chhote/mid-size apps mein Redux ki jagah use karte hain, without extra library.

**If follow-up asked:**
> Kab use karo: Theme, language, logged-in user jaise global data ke liye.  
> Kab nahi: Bahut zyada frequent state changes ke liye (Redux better hai).

---

### TypeScript
**One-liner:** JavaScript ka superset — types add karne se bugs compile time pe pakad aate hain, code zyada readable aur maintainable hota hai.

```ts
interface User {
  id: number;
  name: string;
  email?: string; // optional
}
function greet(user: User): string {
  return `Hello ${user.name}`;
}
```

---

### Micro-frontend
**One-liner:** Bade frontend application ko chhote independent modules mein todna — alag teams alag parts independently develop aur deploy kar sakti hain.

**If follow-up asked:**
> Benefit: Team A aur Team B same project pe kaam kar sakti hain bina ek doosre ke code se conflict ke. Deployment independent rehta hai.

---

### Code Splitting & Lazy Loading
**One-liner:** Code splitting: JS bundle ko chhote pieces mein todna. Lazy loading: components/images tab load karo jab user unhe actually dekhe.

```jsx
const HeavyChart = React.lazy(() => import('./HeavyChart'));

<Suspense fallback={<Spinner />}>
  <HeavyChart />
</Suspense>
```

---

### Monaco Editor
**One-liner:** VS Code ke andar ka wahi editor engine — browser mein embed karo toh users ko VS Code jaisa experience milta hai — syntax highlight, autocomplete sab.

**If follow-up asked:**
> Online Compiler project mein yahi use kiya hai — language selector, code panel, output console as isolated React components.

---

## 🟢 Backend

### Node.js
**One-liner:** JavaScript ko server pe chalane ki runtime — non-blocking, event-driven architecture — APIs, file operations, real-time apps ke liye.

```js
const http = require('http');
const server = http.createServer((req, res) => {
  res.end('Hello from Node!');
});
server.listen(3000);
```

---

### Express.js
**One-liner:** Node.js ke liye minimal web framework — routes banao, middleware use karo, APIs quickly build karo.

```js
app.get('/users', async (req, res) => {
  const users = await User.find();
  res.json(users);
});
```

---

### JWT Authentication
**One-liner:** JSON Web Token — login ke baad server ek encoded token deta hai jo user ki identity prove karta hai. Ye token har API request mein send hota hai.

```
Flow:
1. User login → server JWT banata hai
2. Client localStorage/cookie mein store karta hai
3. Har API call mein: Authorization: Bearer <token>
4. Server verify karta hai → access milta hai
```

```js
const token = jwt.sign({ userId: user._id }, process.env.SECRET, { expiresIn: '7d' });
```

---

### REST API
**One-liner:** Standard tarika client-server communication ka — GET (padhna), POST (banana), PUT (update), DELETE (mitana) — endpoints ke through data exchange.

```js
router.get('/posts', getPosts);       // READ
router.post('/posts', createPost);    // CREATE
router.put('/posts/:id', updatePost); // UPDATE
router.delete('/posts/:id', deletePost); // DELETE
```

---

### Socket.io
**One-liner:** Real-time two-way communication library — WebSocket pe based — chat apps, live notifications, collaborative tools ke liye use hota hai.

```js
// Server
io.on('connection', socket => {
  socket.on('message', data => {
    io.emit('message', data); // sab ko bhejo
  });
});
// Client
socket.emit('message', { text: 'Hello!' });
```

---

### MVC Architecture
**One-liner:** Model (database logic) + View (UI/response) + Controller (business logic) — code ko organized layers mein todne ka standard pattern.

```
/models      → MongoDB schema (User, Post)
/controllers → business logic functions
/routes      → Express routing
```

> Chaibackend project exactly isi architecture pe hai — directly GitHub pe dikhao proof ke taur pe.

---

## 🟡 Database

### MongoDB
**One-liner:** NoSQL document database — data JSON-like objects (documents) mein store hota hai, rigid schema nahi hoti — flexible aur fast for most web apps.

```js
const userSchema = new mongoose.Schema({
  name: { type: String, required: true },
  email: { type: String, unique: true },
  createdAt: { type: Date, default: Date.now }
});
```

---

### Supabase
**One-liner:** Open-source Firebase alternative — PostgreSQL database + Auth + Realtime + Storage, sab REST/SDK ke through accessible.

```js
supabase
  .channel('orders')
  .on('postgres_changes', { event: '*', schema: 'public' }, payload => {
    setData(payload.new);
  }).subscribe();
```

---

### Postman
**One-liner:** API testing tool — backend endpoints ko manually test karo, request bhejo, response dekho — bina frontend banaye API debug karo.

**If follow-up asked:**
> Workflow: Backend banate waqt pehle Postman se test karo — methods, headers, body sab verify karo before frontend integration.

---

## 🔵 Tooling & DevOps

### GitHub Actions / CI-CD
**One-liner:** Har git push pe automatically test/build/deploy hota hai — manual deployment ki zaroorat nahi, consistent process ensure hota hai.

```yaml
name: Deploy
on: [push]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: npm install && npm run build
```

---

### Vercel
**One-liner:** Next.js ke creators ki hosting platform — zero config deployment, automatic preview URLs on every branch, edge functions support.

**If follow-up asked:**
> Next.js ke saath best integration, SSR/SSG automatically handle karta hai, CDN globally distributed hai. Free tier mein bhi preview deployments milti hain.

---

### ESLint
**One-liner:** Code quality tool — automatically code errors, bad patterns, aur style issues dhundta hai — save karte hi ya CI mein.

```json
{
  "extends": ["next/core-web-vitals", "eslint:recommended"],
  "rules": {
    "no-unused-vars": "error",
    "no-console": "warn"
  }
}
```

---

### Git & GitHub
**One-liner:** Git — version control system; GitHub — git repositories online host karne ki platform + collaboration, PRs, CI/CD sab ek jagah.

```bash
git checkout -b feature/new-component  # naya branch
git add . && git commit -m 'feat: add button'
git push origin feature/new-component  # PR ke liye
```

---

### VS Code + GitHub Copilot
**One-liner:** VS Code — daily development editor; GitHub Copilot — AI pair programmer jo code suggestions deta hai inline, boilerplate fast likhta hai.

**If follow-up asked:**
> Copilot se productivity kaafi badhti hai — repetitive patterns, test cases, aur documentation Copilot suggest karta hai. Main isko alpha media ke kaam mein daily use karta hoon.

---

## 🩷 Certifications

### AWS Cloud Practitioner
**One-liner:** AWS ka foundational certification — cloud concepts, basic AWS services (EC2, S3, Lambda), billing, security ke baare mein knowledge.

**If follow-up asked:**
> "Mujhe AWS ka basic understanding hai — EC2 servers ke liye, S3 file storage ke liye, Lambda serverless functions ke liye. Practically main Vercel use karta hoon deployments ke liye." Honest rahon — depth nahi hai advanced mein.

---

## 🚀 Projects

| Project | Stack | Link |
|---------|-------|------|
| Online Code Compiler | Next.js 14, TypeScript, Monaco Editor, Tailwind | [Live ↗](https://online-code-compiler-mocha.vercel.app) |
| Chai Backend — REST API | Node.js, Express.js, MongoDB, JWT | [GitHub ↗](https://github.com/shahbaztube12/chaibackend) |

---

## 🔗 Connect

- GitHub: [@shahbaztube12](https://github.com/shahbaztube12)
- LinkedIn: [Mohd Shahbaz](https://linkedin.com/in/mohd-shahbaz-15a675280)
- Email: shahbaztube9654@gmail.com

---

*Built with ❤️ — React · Next.js · Node.js · TypeScript*
