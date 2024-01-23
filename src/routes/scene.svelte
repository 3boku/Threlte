<script lang="ts">
    import { onMount } from 'svelte'
    import { T } from '@threlte/core'
    import { Grid, OrbitControls } from '@threlte/extras'
    import type { Contributions } from '$lib/types'

    let contributions : Contributions[] = []

    onMount(async () => {
        const response = await fetch('https://gh-contributions-api.vercel.app/mattcroat/2022')
        contributions = await response.json()
        console.log()
    })
</script>

<Grid infiniteGrid sectionColor="#4a4b4a" sectionSize={20} cellSize={20} fadeDistance={400} />

<T.PerspectiveCamera makeDefault postion={[10, 100, 100]} fov={60}>
    <OrbitControls enableDamping autoRotate />
</T.PerspectiveCamera>