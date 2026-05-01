<script module>
  import Button from "$lib/components/Button.svelte";
  import CardContent from "$lib/components/card/card-content.svelte";
  import CardHeader from "$lib/components/card/card-header.svelte";
  import CardTitle from "$lib/components/card/card-title.svelte";
  import Card from "$lib/components/card/card.svelte";
  import Container from "$lib/components/Container.svelte";
  import EmptyContent from "$lib/components/empty/empty-content.svelte";
  import Empty from "$lib/components/empty/empty.svelte";
  import EmptyHeader from "$lib/components/empty/empty-header.svelte";
  import EmptyTitle from "$lib/components/empty/empty-title.svelte";
  import ItemContent from "$lib/components/item/item-content.svelte";
  import Item from "$lib/components/item/item.svelte";

  import { IconPlus, IconTrash, IconX } from "@tabler/icons-svelte";
  import EmptyMedia from "$lib/components/empty/empty-media.svelte";
  import EmptyDescription from "$lib/components/empty/empty-description.svelte";
  import { onMount, tick } from "svelte";
  import Input from "$lib/components/input.svelte";
  import { browser } from "$app/environment";
  import { writable } from "svelte/store";
</script>

<script>
  let todoValue = $state("");
  let todoArray = $state([]);

  onMount(() => {
    const store = localStorage.getItem("todos");
    if (store) todoArray = JSON.parse(store) || [];
  });

  $effect(() => {
    if (browser) {
      localStorage.setItem("todos", JSON.stringify(todoArray));
    }
  });

  function handleAdd() {
    if (!todoValue) return;

    const todoObj = {
      id: crypto.randomUUID(),
      task: todoValue,
      check: false,
    };

    todoArray.push(todoObj);

    todoValue = "";
  }

  function handleDel(id) {
    var elementPos = todoArray
      .map(function (x) {
        return x.id;
      })
      .indexOf(id);
    todoArray.splice(elementPos, 1);
  }
</script>

<div
  class="flex flex-1 flex-col justify-center items-center bg-[url('/bg.png')] bg-no-repeat bg-cover relative before:absolute before:inset-0 before:bg-background/60 overflow-hidden"
>
  <img
    src="https://m1r.ai/7LkWJ.png"
    class="absolute left-5 size-56 animate-fly [--duration:8s]"
    alt="โคมลอย"
  />

  <img
    src="https://m1r.ai/7LkWJ.png"
    class="absolute left-1/2 size-56 animate-fly [--duration:6s]"
    alt="โคมลอย"
  />

  <img
    src="https://m1r.ai/7LkWJ.png"
    class="absolute right-5 size-56 animate-fly [--duration:7s]"
    alt="โคมลอย"
  />

  <Container>
    <div class="grid grid-cols-1 md:grid-cols-2 gap-6 z-10">
      <Card class="md:min-h-160 relative">
        <CardHeader>
          <CardTitle class="font-semibold">ดําเนินการอยู่</CardTitle>
        </CardHeader>
        <div class="px-6">
          <div class="flex items-center gap-2">
            <Input
              placeholder="วันนี้จะทําอะไรดีนะ..."
              bind:value={todoValue}
              onkeydown={(e) => {
                if (e.keyCode === 13) return handleAdd();
              }}
            />
            <Button onclick={handleAdd}>
              <IconPlus />
              เพิ่ม
            </Button>
          </div>
        </div>
        <CardContent
          class="space-y-2 h-full md:max-h-120 no-scrollbar overflow-y-auto"
        >
          {#if !todoArray.filter((i) => !i.check).length}
            <Empty class="border min-h-full">
              <EmptyHeader>
                <EmptyTitle>ยังไม่มีรายการที่ดําเนินการอยู่</EmptyTitle>
                <EmptyDescription>
                  เรามาเริ่มต้นการวางแผนกันเถอะ
                </EmptyDescription>
              </EmptyHeader>
            </Empty>
          {:else}
            {#each todoArray.filter((item) => !item.check) as item}
              <Item size="sm" variant="outline">
                {#snippet child({ props })}
                  <!-- svelte-ignore a11y_invalid_attribute -->
                  <a href="javascript: void(0)" {...props}>
                    <ItemContent
                      class="flex flex-row items-center gap-4"
                      onclick={() => {
                        todoArray.find((i) => i.id === item.id).check =
                          !todoArray.find((i) => i.id === item.id).check;
                      }}
                    >
                      {item.task}
                    </ItemContent>
                    <ItemContent>
                      <Button
                        variant="destructive"
                        size="icon-sm"
                        class="ml-auto"
                        onclick={() => handleDel(item.id)}
                      >
                        <IconTrash />
                      </Button>
                    </ItemContent>
                  </a>
                {/snippet}
              </Item>
            {/each}
          {/if}
        </CardContent>
      </Card>
      <Card class="z-50">
        <CardHeader>
          <CardTitle class="font-semibold">เสร็จสิ้นแล้ว</CardTitle>
        </CardHeader>
        <CardContent class="space-y-2 h-full">
          {#if !todoArray.filter((i) => i.check).length}
            <Empty class="border min-h-full">
              <EmptyHeader>
                <EmptyTitle>ยังไม่มีรายการที่เสร็จสิ้น</EmptyTitle>
                <EmptyDescription>
                  สู้ต่อไป แล้วทําตามที่กําหนดไว้ให้สําเร็จ !
                </EmptyDescription>
              </EmptyHeader>
            </Empty>
          {:else}
            {#each todoArray.filter((item) => item.check) as item}
              <Item size="sm" variant="outline">
                {#snippet child({ props })}
                  <!-- svelte-ignore a11y_invalid_attribute -->
                  <a href="javascript: void(0)" {...props}>
                    <ItemContent
                      class="flex flex-row items-center gap-4"
                      onclick={() => {
                        todoArray.find((i) => i.id === item.id).check =
                          !todoArray.find((i) => i.id === item.id).check;
                      }}
                    >
                      {item.task}
                    </ItemContent>
                    <ItemContent>
                      <Button
                        variant="destructive"
                        size="icon-sm"
                        class="ml-auto"
                        onclick={() => handleDel(item.id)}
                      >
                        <IconTrash />
                      </Button>
                    </ItemContent>
                  </a>
                {/snippet}
              </Item>
            {/each}
          {/if}
        </CardContent>
      </Card>
    </div>
  </Container>
</div>
