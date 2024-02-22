<script lang="ts">
  import Icon from '@iconify/svelte'
  import AppIcon from './lib/AppIcon.svelte'
  import Navbar from './lib/Navbar.svelte'

  // State
  let urlToShareInput = ''

  const generateRedirectUrl = (url: string) => `https://www.youtube.com/redirect?q=${url}`

  const preDefinedLinks = [
    { name: 'Bilibili', href: 'https://www.bilibili.tv' },
  ]

  const links = preDefinedLinks.map(({ name, href }) => ({ name, href: generateRedirectUrl(href) }))

  function onShareClick() {
    navigator.share({ url: generateRedirectUrl(urlToShareInput) })
  }
</script>

<main class="w-full">
  <Navbar/>

  <!-- Quick access -->
  <div class="px-8 mt-16">
    <div class="text-left my-4">
      <h3 class="">Quick access</h3>
    </div>

    <div class="grid grid-cols-4 md:grid-cols-8 lg:grid-cols-12 sm:grid-cols-6 gap-x-4">
      {#each links as link, i}
        <div class="col-span-1">
          <AppIcon name={link.name} href={link.href}/>
        </div>
      {/each}
    </div>
  </div>

  <!-- Share -->
  <div class="px-8 mt-16">
    <div class="text-left my-4">
      <h3 class="">Share URL</h3>
    </div>

    <div class="grid grid-cols-12 gap-x-4">
      <!-- Input and button in same row -->
      <div class="col-span-10">
        <input on:input={(e) => { urlToShareInput = e.target.value }} type="text" class="w-full p-2 border border-gray-300 rounded-md" value=""/>
      </div>
      <div class="col-span-2">
        <button class="w-full p-2 bg-blue-500 text-white rounded-md text-center flex justify-center" on:click={onShareClick}>
          <Icon icon="ooui:share" class="text-2xl"/>
        </button>
      </div>
    </div>
  </div>

</main>