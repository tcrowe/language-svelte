# language-svelte

It's forked from [UnwrittenFun/svelte-atom](https://github.com/UnwrittenFun/svelte-atom) and it only includes the grammar. a.k.a. the syntax highlighting

I first tried to [create a tree-sitter grammar](https://flight-manual.atom.io/hacking-atom/sections/creating-a-grammar/) but it defeated me. If you know how to do that it might be helpful if we can collaborate.

## Table of Contents

+ [Development](#development)
+ [Production](#production)
+ [Copying, license, and contributing](#copying-license-and-contributing)

## Development

To test locally clone the repository and `apm link` in it.

Reference [./test/svelte-syntax-test.svelte](./test/svelte-syntax-test.svelte) for viewing how the editor response to the grammar file in [./grammars/svelte.json](./grammars/svelte.json).

## Production

`npm run prd`

## Copying, license, and contributing

Copyright (C) Tony Crowe 2020 <https://tcrowe.github.io/contact/>

Thank you for using and contributing to make language-svelte better.

⚠️ Please run `npm run prd` before submitting a patch.

⚖️ language-svelte inherits MIT license from parent project [UnwrittenFun/svelte-atom](https://github.com/UnwrittenFun/svelte-atom)
