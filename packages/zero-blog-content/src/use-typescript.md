ts-node unexpected token 'export'
exports is not defined in ES module scope
https://github.com/TypeStrong/ts-node/issues/935
use tsx typescriptexecute

array, undefined is not assignable to type
https://github.com/microsoft/TypeScript/issues/55206

How to Setup Node.js with TypeScript in 2023
https://www.youtube.com/watch?v=H91aqUHn8sE

https://fab1o.medium.com/named-parameters-in-typescript-288d90f35639

youtube lydia halli

foundations are everything, fundamentals
https://www.epicweb.dev/why-i-wont-use-nextjs

implicit testing
web dev simplified

be careful with select defaultvalues and delayed render, just use value, useEffect bug
https://github.com/react-hook-form/react-hook-form/issues/1558

https://www.epicweb.dev/why-i-wont-use-nextjs

never[] incompatible with IServiceMeta[]
const initialInputs = {
counterName: '',
service: [] as IServiceMeta[],
priorityLevel: InitialPriorityLevelsString[0],
}

https://github.com/skillrecordings/products
https://github.com/vercel/turbo/tree/main/examples/kitchen-sink

https://steveholgado.com/typescript-types-from-arrays/
https://github.com/microsoft/TypeScript/issues/28046
const animals = ['cat', 'dog', 'mouse'] as const
type Animal = (typeof animals)[number]

https://stackoverflow.com/questions/45894524/getting-type-of-a-property-of-a-typescript-class-using-keyof-operator
type BarType = FooType['bar'];
type FooType = {
bar: string;
}

array reduce
const array1 = [1, 2, 3, 4];
// 0 + 1 + 2 + 3 + 4
const initialValue = 0;
const sumWithInitial = array1.reduce(
(accumulator, currentValue) => accumulator + currentValue,
initialValue,
);
console.log(sumWithInitial);
// Expected output: 10

- use memo
  http://www.shuang.email/question/9;jsessionid=F8FD2C94338987BCE430BD19DA859842

```
    const Team = ({ id, name, active }) => {
    // memoize calling `createTeam` because it's
    // an expensive operation
    const team = useMemo(() => createTeam({ id, name, active }), [
     id,
     name,
     active,
    ])
    const [players, setPlayers] = useState([])
    useEffect(() => {
     if (team.active) {
       getPlayers(team).then(setPlayers)
     }
    }, [team])
    return <Players team={team} players={players} />
    }
```

https://github.com/soldair/node-qrcode

https://stackoverflow.com/questions/47892127/succinct-concise-syntax-for-optional-object-keys-in-es6-es7
...flag1 && { optionalKey1: 5 },
let flag1 = true;
let flag2 = false;
// extra cases added by Abdull
let optionalKey8 = 8;
let optionalKey9 = undefined;
let optionalKey10 = false;
let optionalKey11 = null;
let optionalKey12 = "twelve";
const obj = {
requiredKey1: 1,
requiredKey2: 2,
...(flag1 && { optionalKey3: 3 }),
...(flag2 && { optionalKey4: 4, optionalKey5: 5 }), // ignored
...(flag1 && { optionalKey6: 6, optionalKey7: 7 }),
...(optionalKey8 && { optionalKey8 }),
...(optionalKey9 && { optionalKey9 }), // ignored
...(optionalKey10 && { optionalKey10 }), // ignored
...(optionalKey11 && { optionalKey11 }), // ignored
...(optionalKey12 && { optionalKey12 })
};
console.log(obj);

turbo start --filter=boc_queue_api

# express

https://github.com/w3tecch/express-typescript-boilerplate
https://www.geeksforgeeks.org/explain-error-handling-in-express-js-using-an-example/

ERR_REQUIRE_ESM
https://antfu.me/posts/publish-esm-and-cjs
{
"name": "my-cool-package",
"main": "./dist/index.js",
"module": "./dist/index.mjs",
"types": "./dist/index.d.ts",
"exports": {
".": {
"require": "./dist/index.js",
"import": "./dist/index.mjs",
"types": "./dist/index.d.ts"
}
},
"scripts": {
"build": "tsup src/index.ts --format cjs,esm --dts --clean",
"watch": "npm run build -- --watch src",
"prepublishOnly": "npm run build"
}
}

args or params
https://levelup.gitconnected.com/how-to-write-named-parameters-in-typescript-f05d5031dec6

https://www.basedash.com/blog/generic-arrow-functions-in-typescript
const identity = <T>(arg: T): T => {
return arg;
}
https://github.com/microsoft/TypeScript/issues/15713
const f = <T,>(arg: T): T => {...}

https://stackoverflow.com/questions/28975896/is-there-a-way-to-check-for-both-null-and-undefined
if (x == null) {

https://express-validator.github.io/docs/
https://joi.dev

https://github.com/TypeStrong/ts-node/issues/935

https://www.webdevolution.com/blog/remove-null-values-from-array-javascript
const array = [1, 2, 3, null, " ", , undefined, 4, "Text", 0, false, true];
const removeEmptyValues = array => {
const filtered = array.filter(e => e);
const filtered = array.filter(x => x !== null);
// For typescript inferrence
// https://stackoverflow.com/questions/43118692/typescript-filter-out-nulls-from-an-array
return filtered;
};
// returns [ 1 , 2 , 3 , 4 , 'Text' , true ]

tsup incremental bug
update tsconfig.json, `"incremental": false,`
https://github.com/egoist/tsup/issues/884

git clone subdirectory
downgit
git sparse
pnpm dlx create-turbo@latest --example [example-name]
pnpm dlx create-turbo@latest --example kitchen-sink

## next and tsup together

jsx was set to preserve (next.js implements its own optimized jsx transform)

`./tsup.tsconfig.json`

```
{
  "compilerOptions": {
    "jsx": "react-jsx",
  }
}
```

`tsup.config.ts`

```
export default defineConfig(options => ({
  tsconfig: './tsup.tsconfig.json',
  ...options,
}))
```

# vscode extensions

- yoavbls.pretty-ts-errors

# Element implicitly has an type because expression of type can't be used to index type, object string index

# react-hook-form, A component is changing an uncontrolled input to be controlled

https://github.com/colinhacks/zod/issues/3114
don't use `required_error`, use min 1

```
const schema: ZodType<FormData> = z.object({
  firstName: z.string().min(1, { message: "First Name is required" })
});
```

# boolean variables naming convention

https://dev.to/michi/tips-on-naming-boolean-variables-cleaner-code-35ig

# tsup

https://johnnyreilly.com/dual-publishing-esm-cjs-modules-with-tsup-and-are-the-types-wrong
https://arethetypeswrong.github.io
https://github.com/arethetypeswrong/arethetypeswrong.github.io/issues/169
https://www.npmjs.com/package/@arethetypeswrong/cli

# lru-cache Private identifiers are only available when targeting ECMAScript 2015 and higher.

tsconfig.json

```
{
  "compilerOptions": {
    "moduleResolution": "Node",
    "target": "ES6",
    "outDir": "dist",
    "rootDir": "src",
    "esModuleInterop": true,
    "lib": ["esnext"],
    "strict": true,
    "skipLibCheck": true
  },
  "include": ["src/**/*"],
  "exclude": ["node_modules"]
}
```

# ts-node Unknown file extension ".ts"
https://github.com/TypeStrong/ts-node/issues/2100

# tsx __dirname is not defined in ES module scope

https://iamwebwiz.medium.com/how-to-fix-dirname-is-not-defined-in-es-module-scope-34d94a86694d
https://flaviocopes.com/fix-dirname-not-defined-es-module-scope/