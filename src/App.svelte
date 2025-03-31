<script>
  import datas from './lib/movies'
  import Navbar from './lib/components/Navbar.svelte';
  import Modal from './lib/components/Modal.svelte';
  import Movies from './lib/components/Movies.svelte';


  let movieData = $state(datas);
  let isModal = $state(false);// 모달창 변수 추가
  let selectedMovie = $state(0); // 선택한 영화의 인덱스 변수 추가
  const handleLike = (i) => {
    movieData[i].likeCount += 1;
  }
  const closeModal = () => {
    isModal = false;
  }

  const openModal = (i) => {
    isModal = true;
    selectedMovie = i;
  }

  // 이벤트창 표시 여부
  let isEvent = $state(true);
</script>

<Navbar />
<div class={isEvent ? 'event show' : 'event'}>
  <p>NETPLIX 강렬한 운명의 드라마, 경기크리처</p>
  <button>X</button>
</div>

<Movies movieData={movieData} handleLike={handleLike} openModal={openModal}/>

{#if isModal}
  <Modal movieData={movieData} {selectedMovie} {closeModal}/>
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
