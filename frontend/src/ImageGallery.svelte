<script lang="ts">
  import { Streamlit, setStreamlitLifecycle } from "./streamlit";
  setStreamlitLifecycle();

  export let imageUrls: Array<string>;
  export let height: number;

  let selectedImageUrl: string;

  function image_onclick(event: any) {
    selectedImageUrl = event.srcElement.currentSrc;
    Streamlit.setComponentValue(selectedImageUrl);
  }
</script>


<div class="scroller">
  {#each imageUrls as imageUrl}
      <img src={imageUrl} id={imageUrl} alt="" style="height: {height}px;" on:click={image_onclick}>
  {/each}
</div>


<style>
  .scroller {
    min-height: 100px;
    overflow-x: scroll;
    overflow-y: hidden;
    white-space: nowrap;
  }
	img { 
    display: inline-block;
    padding: 1%;
    border-radius: 20px;
    opacity: 0.9; 
    transition: all .2s; 
  }

	img:hover { 
    opacity: 1; 
    transform: scale(1.05); 
    cursor: pointer;
  }
</style>






