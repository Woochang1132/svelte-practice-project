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
</script>

<Navbar />
<Movies movieData={movieData} handleLike={handleLike} openModal={openModal}/>

{#if isModal}
  <Modal movieData={movieData} {selectedMovie} {closeModal}/>
{/if}
<style>
</style>
