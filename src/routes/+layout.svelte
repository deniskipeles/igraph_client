<script>
	import Header from './../lib/components/Header.svelte';
    import { supabaseClient } from '$lib/supabaseClient'
    import { invalidate } from '$app/navigation'
    import { onMount } from 'svelte'
    import './styles.css'

    onMount(() => {
        const {
            data: { subscription }
        } = supabaseClient.auth.onAuthStateChange(() => {
            invalidate('supabase:auth')
        })

        return () => {
            subscription.unsubscribe()
        }
    })
</script>

<Header/>
<div class="container" style="padding: 50px 0 100px 0">
    <slot />
</div>