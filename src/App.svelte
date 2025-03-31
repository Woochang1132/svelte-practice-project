<script>
  import datas from './lib/movies'
  import Navbar from './lib/components/Navbar.svelte';
  import Modal from './lib/components/Modal.svelte';
  import Movies from './lib/components/Movies.svelte';
  import AddTansition from './lib/components/AddTansition.svelte';
  import SearchBar from './lib/components/SearchBar.svelte';



  let movieData = $state(datas);
  let isModal = $state(false);// 모달창 변수 추가
  let selectedMovie = $state(0); // 선택한 영화의 인덱스 변수 추가
  let data_temp = $state([...datas]);
  let alertText = $state('');
  const handleLike = (id) => {
    // movieData[i].likeCount += 1;
    datas.map(movie => {
      if(movie.id === id){
        movie.likeCount += 1;
      }
    });
    data_temp = [...datas];
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
  const AddTansitionFunc = () => {
    isEvent = false
  }
  //  영화 전체 목록을 보기 위한 방법
  const movieListAll = () => {
    data_temp = [...movieData];
    alertText = ''
  }

</script>

<Navbar />
<AddTansition isEvent={isEvent} AddTansitionFunc={AddTansitionFunc}/>
<SearchBar movieData={movieData} bind:data_temp={data_temp} bind:alertText={alertText}/>
<button on:click={() => { movieListAll() }}>전체보기</button>
<Movies data_temp={data_temp} movieData={movieData} handleLike={handleLike} openModal={openModal}/>

{#if isModal}
  <Modal movieData={movieData} {selectedMovie} {closeModal}/>
{/if}
<style></style>
