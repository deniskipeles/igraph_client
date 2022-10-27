<div>
    <h1>home page</h1>
</div>



<script>
    import {supabaseClient} from "$lib/supabaseClient.js";
     const listUsers = async ()=>{
        
        let { data: users, error } = await supabaseClient
        .from('user_icon_analysis')
        .select(`
        followers_or_graphers,
            icons (
                id
            )
        `)

        
        const {data:user,error:getUserError} = await supabaseClient.auth.getUser()
        console.log(user)


        console.log(users)
        console.log(error)
    }
    listUsers()
</script>