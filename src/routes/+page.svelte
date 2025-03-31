<script lang="ts">
  import { AlertDialog, DropdownMenu } from "bits-ui";

  let open = $state(false);
  let input: HTMLInputElement | undefined = $state();

  $effect(() => {
    if (input) {
      setTimeout(() => {
        input?.focus();
      }, 0);
    }
  });
</script>

<button class="border" onclick={() => (open = true)}>Open alert dialog</button>

<DropdownMenu.Root>
  <DropdownMenu.Trigger class="border">Open dropdown menu</DropdownMenu.Trigger>
  <DropdownMenu.Portal>
    <DropdownMenu.Content>
      <DropdownMenu.Item onclick={() => (open = true)}>
        Open alert dialog
      </DropdownMenu.Item>
    </DropdownMenu.Content>
  </DropdownMenu.Portal>
</DropdownMenu.Root>

<AlertDialog.Root bind:open>
  <AlertDialog.Portal>
    <AlertDialog.Content
      class="fixed left-1/2 top-1/2 z-50 -translate-x-1/2 -translate-y-1/2 w-40 h-40 border bg-gray-500"
    >
      Alert dialog content
      <input bind:this={input} class="border" />
    </AlertDialog.Content>
  </AlertDialog.Portal>
</AlertDialog.Root>
