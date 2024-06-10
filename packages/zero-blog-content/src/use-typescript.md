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

# expressjs logging

morgan
winston
