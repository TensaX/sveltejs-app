<script>
    export let href
</script>

<a {href} class="text-black flex items-center justify-center bg-gray-200 border-0 px-8 focus:outline-none hover:bg-gray-300 custom rounded ">
    <slot />
</a>

<style>
    a{
        font-size: 150%;
    }
    a:hover{
        font-size: 160%;
    }
</style>