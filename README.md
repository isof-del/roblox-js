Roblox JavaScript → Luau
An experimental JavaScript development toolchain for Roblox that compiles JavaScript source into Luau-oriented output.
> **Status:** Experimental. JavaScript compatibility is incomplete, and the generated output should be treated as a development target rather than a guarantee of full JavaScript semantics.
What is in this repository?
The project currently contains a TypeScript compiler/emitter, a JavaScript compatibility runtime, a browser playground, a small project API, database schema code, and compiler scripts.
Highlights
JavaScript parsing through Acorn
JavaScript → Luau code emission
Runtime compatibility helpers for JavaScript-style behavior
Classes and inheritance handling
Destructuring support
`for...of` and `for...in`
Imports and exports
Array and string helpers
`Map` and `Set` support
JSON helpers
Compiler diagnostics and statistics
Project compilation with Luau output
Generated `default.project.json` for a Rojo-oriented workflow
Web playground and project UI
Repository layout
```text
.
├── .github/             # GitHub issue templates and repository metadata
├── docs/                # Project documentation
├── examples/            # Small source examples
├── scripts/             # Compiler smoke/integration scripts
├── src/
│   ├── app/             # Next.js app, API routes, docs, playground, projects
│   ├── components/      # React UI components
│   ├── compiler/        # JavaScript → Luau compiler and runtime
│   └── db/              # Drizzle database schema/access
├── .gitignore
├── CONTRIBUTING.md
├── LICENSE
├── package.json
├── tsconfig.json
└── README.md
```
Requirements
Use a current Node.js release compatible with the dependencies in `package.json`.
Install
```bash
npm install
```
Run the web app
```bash
npm run dev
```
Then open the local URL printed by Next.js.
Build and verify
```bash
npm run typecheck
npm run lint
npm run build
```
Compiler smoke scripts:
```bash
npx tsx scripts/test-compiler.ts
npx tsx scripts/test-multi.ts
```
Compiler API
The main compiler entry point is `src/compiler/index.ts`.
At a high level:
```ts
import { compileFile, compileProject } from "./src/compiler";

const result = compileFile(
  `const x = 1 + 2;`,
  "main.js",
  { target: "script" },
);

console.log(result.code);
```
For multi-file projects, `compileProject` produces Luau outputs, the compatibility runtime when needed, and a `default.project.json` file.
Compatibility notes
This project is not a drop-in replacement for the JavaScript language or the Roblox Luau runtime. Some JavaScript features are intentionally unsupported or require compatibility helpers.
Treat compiler output as generated code. Do not hand-edit generated `.luau` files when those files will be regenerated from their JavaScript sources.
Rojo workflow
The project can emit a `default.project.json` intended for a Rojo-oriented layout. The generated project configuration should be reviewed before using it in a production Roblox project.
Contributing
See CONTRIBUTING.md for setup, testing, and pull-request guidance.
License
No license has been declared yet. See LICENSE. The placeholder should be replaced with the final license chosen by the copyright holder before public redistribution or accepting contributions under explicit open-source terms.
