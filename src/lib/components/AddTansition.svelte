<script>
      import { fade, fly } from 'svelte/transition';
      export let isEvent; //전달받은 transition 이벤트 여부
      export let AddTansitionFunc;
</script>

{#if isEvent}
  <div in:fly={{y:-400, duration:1000}} out:fade class='event show'>
    <p>NETPLIX 강렬한 운명의 드라마, 경기크리처</p>
    <!-- svelte-ignore event_directive_deprecated -->
    <button on:click={() => {AddTansitionFunc()}}>X</button>
  </div>
{/if}


<style>
 .event{
  width: 100%;
  background: #666;
  padding: 5px 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  color: #fff;
  text-align: center;
  margin-bottom: 1em;

  /* 창이 보이지 않게 */
  max-height: 0px;
  opacity: 0;
  overflow: hidden;
  transition: all 0.4s;
}

  /* 기본 창이 보이게 */
  .show{
    opacity: 1;
    max-height: 100px;
  }

  .event button{
    padding: 2px;
  }
</style>