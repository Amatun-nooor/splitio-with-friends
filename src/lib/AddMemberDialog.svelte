<script lang="ts">
	import Dialog, { Title, Content, Actions } from '@smui/dialog';
	import Button, { Label } from '@smui/button';
	import Textfield from '@smui/textfield';

	export let openDialog: boolean;
	export let addCallback: (name: string) => void;

	let inputName: string = '';
</script>

<Dialog
	bind:open={openDialog}
	aria-labelledby="default-focus-title"
	aria-describedby="default-focus-content"
>
	<Title id="default-focus-title">👋 add someone</Title>
	<Content id="default-focus-content">
		<div>
			enter their name:
			<Textfield bind:value={inputName} />
		</div>

		<p>⚠️ once added, <strong>you can't edit nor delete a member</strong>, so choose wisely!</p>
	</Content>
	<Actions>
		<Button>
			<Label>cancel</Label>
		</Button>
		<Button
			variant="unelevated"
			disabled={inputName === ''}
			on:click={() => {
				addCallback(inputName);
				inputName = '';
			}}
		>
			<Label>add</Label>
		</Button>
	</Actions>
</Dialog>
