<script>
  import { IconBrandHeadlessui, IconListCheck, IconPlant, IconTorii } from "@tabler/icons-svelte";
  import Button, { buttonVariants } from "./Button.svelte";
</script>

<header class="px-4 md:px-6 bg-[#ff8fab] sticky top-0">
  <div
    class="max-w-340 mx-auto w-full px-4 sm:px-6 flex justify-between h-14 items-center gap-4"
  >
    <div class="flex items-center gap-2">
      <div class="flex items-center gap-6">
        <a
          class="text-white font-semibold flex items-center gap-2"
          href="/">
          <IconBrandHeadlessui size="18" />
          Panuri</a
        >
      </div>
    </div>
    <div class="flex items-center gap-2">
      <button
        onclick={(window.location.href = "/")}
        class="mx-3 inline-flex items-center gap-2 cursor-pointer"
      >
        <IconListCheck class="size-4" />
        Todo List</button
      >
      <button
        onclick={(window.location.href = "/tanabata")}
        class="mx-3 inline-flex items-center gap-2 cursor-pointer"
      >
        <IconPlant class="size-4" />
        Blessing
      </button>
    </div>
    <div class="flex items-center">
      <Button variant="outline">
        <IconTorii />
        Group 3
      </Button>
    </div>
  </div>
</header>
