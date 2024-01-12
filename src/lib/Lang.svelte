
<script lang="ts">
    import { goto } from "$app/navigation"
	import { Avatar, popup } from "@skeletonlabs/skeleton";
    let language = [
          { name: "en", href:"/", icon: "https://cdn1.iconfinder.com/data/icons/world-flags-circular/1000/Flag_of_United_Kingdom_-_Circle-512.png"},
          { name: "vn",href:"/vn",  icon:"https://cdn-icons-png.flaticon.com/512/323/323319.png" },
          { name: "de",href:"/de",icon:"https://cdn-icons-png.flaticon.com/512/4628/4628643.png" }
        ];


    </script>
    

    <button class="btn  btn-sm variant-soft-primary " use:popup={{ event: 'click', target: 'language', closeQuery: 'a[href]' }}>
        <i class="fa-solid fa-palette text-lg md:!hidden" />
        <span class="">
            <i class="fa-regular fa-globe"></i>
        </span>
        <i class="fa-solid fa-caret-down opacity-50" />
    </button>
    <div class="card p-4  shadow-xl" data-popup="language">
        <nav class="list-nav  overflow-y-auto">
                <ul>
                    <!-- , badge -->
                    {#each language as { icon, name,href }}
                        <li>
                            <button
                                class="option w-full h-full"
                                type="submit"
                                name="language"
                                value={name}
                                on:click={() => goto(href)}
                            >
                                <span>
                                    <Avatar src={icon} width="w-4" rounded="rounded-full"/>
                                    
                                </span>
                                <!-- {#if badge}<span class="badge variant-filled-secondary">{badge}</span>{/if} -->
                            </button>
                        </li>
                    {/each}
                </ul>
        </nav>
        </div>