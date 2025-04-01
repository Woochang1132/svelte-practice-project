<script>
  import { onMount, onDestroy } from 'svelte';
  import datas from './lib/movies'
  import Navbar from './lib/components/Navbar.svelte';
  import Modal from './lib/components/Modal.svelte';
  import Movies from './lib/components/Movies.svelte';
  import AddTansition from './lib/components/AddTansition.svelte';
  import SearchBar from './lib/components/SearchBar.svelte';

  // 이벤트 텍스트
  const eventText = $state([
    "영화 정보 업데이트",
    "신규 영화 추가",
    "이벤트 진행중"
  ]);
  let movieData = $state(datas);
  let isModal = $state(false);// 모달창 변수 추가
  let selectedMovie = $state(0); // 선택한 영화의 인덱스 변수 추가
  let data_temp = $state([...datas]);
  let alertText = $state('');
    // 이벤트창 표시 여부
  let isEvent = $state(true);
  let eventIndex = $state(0);
  let intervalEventText;
  const handleLike = (id) => {
    // movieData[i].likeCount += 1;
    movieData.map(movie => {
      if(movie.id === id){
        movie.likeCount += 1;
      }
    });
    // data_temp = [...datas];
    // 목적 : data_temp 있는 내용만 필터링 필요
    data_temp = movieData.filter(movie => {
      return data_temp.includes(movie);
    })
  }
  const closeModal = () => {
    isModal = false;
  }

  const openModal = (i) => {
    isModal = true;
    selectedMovie = i;
  }

  const AddTansitionFunc = () => {
    isEvent = false
  }
  //  영화 전체 목록을 보기 위한 방법
  const movieListAll = () => {
    data_temp = [...movieData];
    alertText = ''
  }

  $effect(() => {
    clearInterval(intervalEventText);
    intervalEventText = setInterval(() => {
      eventIndex += 1
      if(eventIndex >= eventText.length){
        eventIndex = 0;
      }
    }, 3000)
  });

</script>

<Navbar />
<AddTansition isEvent={isEvent} AddTansitionFunc={AddTansitionFunc} eventText={eventText} eventIndex={eventIndex}/>
<SearchBar movieData={movieData} bind:data_temp={data_temp} bind:alertText={alertText}/>
<button on:click={() => { movieListAll() }}>전체보기</button>
<Movies data_temp={data_temp} movieData={movieData} handleLike={handleLike} openModal={openModal}/>

{#if isModal}
  <Modal movieData={movieData} {selectedMovie} {closeModal}/>
{/if}
<style></style>
