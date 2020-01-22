<!--

These are copy and pasted examples from: https://svelte.dev/docs

⚠️ The code doesn't work and it's not supposed to work. It's only for checking
if the ../grammar/svelte.json works.

-->

<script context="module">
const one = "two";
</script>

<script>
const three = "four";
</script>

<style>
.test-css-class {
  border: 1px solid red;
}
</style>

<!-- Tags -->
<div class="test-css-class">ok!</div>

<!-- Attributes and props -->
<div class="foo">
	<button disabled>can't touch this</button>
</div>

<input type=checkbox>

<a href="page/{p}">page {p}</a>

<button disabled={!clickable}>button text</button>
<button disabled="{number !== 42}">...</button>
<button disabled={disabled}>...</button>
<button {disabled}>...</button>

<Widget foo={bar} answer={42} text="hello"/>
<Widget {...things}/>
<Widget {...$$props}/>

<!-- Text expressions -->

<h1>Hello {name}!</h1>
<p>{a} + {b} = {a + b}.</p>

<!-- Comments -->
<!-- svelte-ignore a11y-autofocus -->
<input bind:value={name} autofocus>

<!-- {#if ...} -->
{#if answer === 42}
	<p>what was the question?</p>
{/if}
{#if porridge.temperature > 100}
	<p>too hot!</p>
{:else if 80 > porridge.temperature}
	<p>too cold!</p>
{:else}
	<p>just right!</p>
{/if}

<!-- {#each ...} -->
<h1>Shopping list</h1>
<ul>
	{#each items as item}
		<li>{item.name} x {item.qty}</li>
	{/each}
</ul>
{#each items as item, i}
	<li>{i + 1}: {item.name} x {item.qty}</li>
{/each}
{#each items as item, i (item.id)}
	<li>{i + 1}: {item.name} x {item.qty}</li>
{/each}
{#each items as { id, name, qty }, i (id)}
	<li>{i + 1}: {name} x {qty}</li>
{/each}
{#each objects as { id, ...rest }}
	<li><span>{id}</span><MyComponent {...rest}/></li>
{/each}
{#each items as [id, ...rest]}
	<li><span>{id}</span><MyComponent values={rest}/></li>
{/each}
{#each todos as todo}
	<p>{todo.text}</p>
{:else}
	<p>No tasks today!</p>
{/each}

<!-- {#await ...} --> 
{#await promise}
	<!-- promise is pending -->
	<p>waiting for the promise to resolve...</p>
{:then value}
	<!-- promise was fulfilled -->
	<p>The value is {value}</p>
{:catch error}
	<!-- promise was rejected -->
	<p>Something went wrong: {error.message}</p>
{/await}
{#await promise}
	<!-- promise is pending -->
	<p>waiting for the promise to resolve...</p>
{:then value}
	<!-- promise was fulfilled -->
	<p>The value is {value}</p>
{/await}
{#await promise then value}
	<p>The value is {value}</p>
{/await}

<!-- {@html ...} -->
<div class="blog-post">
	<h1>{post.title}</h1>
	{@html post.content}
</div>

<!-- {@debug ...} -->
{@debug user}
{@debug user1, user2, user3}
{@debug user.firstname}
{@debug myArray[0]}
{@debug !isReady}
{@debug typeof user === 'object'}

<!-- Element directives -->
<button on:click={handleClick}>
	count: {count}
</button>
<button on:click="{() => count += 1}">
	count: {count}
</button>
<form on:submit|preventDefault={handleSubmit}>
	<!-- the `submit` event's default is prevented,
		 so the page won't reload -->
</form>
<button on:click>
	The component itself will emit the click event
</button>
<button on:click={increment} on:click={track}>Click me!</button>

<!-- bind:property -->
<input bind:value={name}>
<textarea bind:value={text}></textarea>
<input type="checkbox" bind:checked={yes}>
<input bind:value={value}>
<input bind:value>
<input type="number" bind:value={num}>
<input type="range" bind:value={num}>
<select bind:value={selected}>
	<option value={a}>a</option>
	<option value={b}>b</option>
	<option value={c}>c</option>
</select>
<select multiple bind:value={fillings}>
	<option value="Rice">Rice</option>
	<option value="Beans">Beans</option>
	<option value="Cheese">Cheese</option>
	<option value="Guac (extra)">Guac (extra)</option>
</select>
<video
	src={clip}
	bind:duration
	bind:buffered
	bind:seekable
	bind:seeking
	bind:played
	bind:ended
	bind:currentTime
	bind:paused
	bind:volume
	bind:videoWidth
	bind:videoHeight
></video>

<!-- bind:group --> 
<input type="radio" bind:group={tortilla} value="Plain">
<input type="radio" bind:group={tortilla} value="Whole wheat">
<input type="radio" bind:group={tortilla} value="Spinach">
<input type="checkbox" bind:group={fillings} value="Rice">
<input type="checkbox" bind:group={fillings} value="Beans">
<input type="checkbox" bind:group={fillings} value="Cheese">
<input type="checkbox" bind:group={fillings} value="Guac (extra)">

<!-- bind:this -->
<canvas bind:this={canvasElement}></canvas>

<!-- class:name -->
<div class="{active ? 'active' : ''}">...</div>
<div class:active={active}>...</div>
<div class:active>...</div>
<div class:active class:inactive={!active} class:isAdmin>...</div>

<!-- use:action -->
<div use:foo></div>
<div use:foo={bar}></div>

<!-- transition:fn -->
<div transition:fade>fades in and out</div>
<div transition:fade="{{ duration: 2000 }}">
  flies in, fades out over two seconds
</div>
<div in:whoosh>whooshes in</div>
<p in:typewriter="{{ speed: 20 }}">
  The quick brown fox jumps over the lazy dog
</p>
<p
		transition:fly="{{ y: 200, duration: 2000 }}"
		on:introstart="{() => status = 'intro started'}"
		on:outrostart="{() => status = 'outro started'}"
		on:introend="{() => status = 'intro ended'}"
		on:outroend="{() => status = 'outro ended'}"
	>
		Flies in and out
	</p>
  
<!-- in:fn/out:fn -->
<div in:fly out:fade>flies in, fades out</div>

<!-- animate:fn -->
<li animate:flip>{item}</li>
<li animate:flip="{{ delay: 500 }}">{item}</li>
<div animate:whizz>{item}</div>

<!-- <slot> -->
<slot/>
<slot></slot>
<slot name="header"></slot>
<slot name="footer"></slot>
<FancyList {items} let:item={item}>
	<div>{item.text}</div>
</FancyList>
<ul>
	{#each items as item}
		<li class="fancy">
			<slot item={item}></slot>
		</li>
	{/each}
</ul>

<!-- <svelte:self> -->
<svelte:self count="{count - 1}"/>

<!-- <svelte:component> -->
<svelte:component this={currentSelection.component} foo={bar}/>

<!-- <svelte:window> -->
<svelte:window on:keydown={handleKeydown}/>
<svelte:window bind:scrollY={y}/>

<!-- <svelte:body> -->
<svelte:body
	on:mouseenter={handleMouseenter}
	on:mouseleave={handleMouseleave}
/>

<!-- <svelte:head> -->
<svelte:head>
	<link rel="stylesheet" href="tutorial/dark-theme.css">
</svelte:head>

<!-- <svelte:options> -->
<svelte:options tag="my-custom-element"/>