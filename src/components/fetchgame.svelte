<script>
  import { onMount } from "svelte";
  import Gamestag from "./gamestag.svelte";
  let url =
    "https://sabz.herokuapp.com/https://www.dlfox.com/wp-json/wp/v2/posts";
  let games = [];

  onMount(async () => {
    let res = await fetch(url);
    let data = await res.json();
    games = data;
  });
</script>

<div class="container">
  <div class="row">
    {#each games as game, i}
      <div class="col-12 col-sm-6 card ">
        <!-- <div class="card-title  border">{@html game.title.rendered}</div> -->
        <div class="card-body   border m-4">
          {@html game.content.rendered}

          <div class="  d-flex  ">
            <div class="   text-dark  p-2   ">
              <Gamestag g={game.content.rendered} />
            </div>
            <button type="button" class="btn btn-outline-primary   btn-lg     ">
              اضافه به سبد
              <i class="fas fab fa-shopping-cart" />
            </button>
          </div>
        </div>
      </div>
    {/each}
  </div>
</div>
