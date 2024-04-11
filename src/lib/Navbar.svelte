<script lang="ts">
  import Icon from '@iconify/svelte'

  function addNewQuickAccess() {
    console.log('Add new quick access')
    const url = prompt('Enter the URL:')
    if (!url) return

    let name = prompt('Enter the name of the quick access') || url

    const currentData = window.localStorage.getItem('ITESLA_DISPLAY_QUICKACCESS')
    const json = JSON.parse(currentData || '[]')
    window.localStorage.setItem('ITESLA_DISPLAY_QUICKACCESS', JSON.stringify([...json, { name, href: url }]))
  }
</script>

<nav class="px-8 py-4 fixed top-0 left-0 w-full bg-zinc-800">
  <div class="grid grid-cols-2">
    <div class="">
      <!-- Title -->
      <p class="text-white">Tesla dashboard</p>
    </div>
    <div class="flex justify-end text-blue-500 text-xl">
      <button class="" on:click={addNewQuickAccess}>
        <Icon icon="ooui:add" class=""/>
      </button>
    </div>
  </div>
</nav>