<script lang="ts">
  export let name: string
  export let href: string = '#'
</script>

<a class="block" href={href}>
  <div class="flex justify-center items-center w-full aspect-square bg-slate-500 rounded-md shadow-lg hover:scale-105">
    <p class="text-4xl font-bold">{name.charAt(0).toUpperCase()}</p>
  </div>
  <p class="text-center pt-2">{name}</p>
</a>