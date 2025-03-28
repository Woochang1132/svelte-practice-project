<script>
  import logo1 from './assets/svelte.svg'
  import datas from './lib/movies'
  import Navbar from './lib/components/Navbar.svelte';
  import Modal from './lib/components/Modal.svelte';

  let isModal = false; // 모달창 변수 추가
  let selectedMovie = 0; // 선택한 영화의 인덱스 변수 추가
  const handleLike = (i) => {
    datas[i].likeCount += 1;
  }
  const handleOpenModal = (i) => {
     isModal = true;
     selectedMovie = i;
  }
  const closeModal = () => {
    isModal = false;
  }
</script>

<Navbar/>
<main class="container">
  <h1>영화정보</h1>
  <img src={logo1} alt="">
  <img src="/vite.svg" alt="">
  {#each datas as data, i}
  <div class="item">
    <figure>
      <img src={data.imgUrl} alt={data.title}>
    </figure>
    <div class="info">
      <h3 class="bg-yellow">{data.title}</h3>
      <p>개봉: {data.year}</p>
      <p>장르: {data.category}</p>
      <button on:click={() => {handleLike(i)}}>좋아요 {data.likeCount}</button>
      <button class="btn btn-primary" on:click={() => {handleOpenModal(i)}}>상세보기</button>
    </div>
  </div>
  {/each}
</main>

{#if isModal}
  <Modal {datas} {selectedMovie} {closeModal}/>
{/if}
<style>
.bg-yellow{
  background: gold;
  padding: 10px;
  color: #333;
}
.item {
  width: 100%;
  border: 1px solid #ccc;
  display: flex;
  margin-bottom: 20px;
  padding: 1rem;
}

.item figure{
  width: 30%;
  margin-right: 1rem;
}

.item img{
  width: 100%;
}

.item .info{
  width: 100%;
}


</style>
