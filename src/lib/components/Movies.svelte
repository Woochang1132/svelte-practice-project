<script>
    export let movieData;
    export let handleLike;
    export let openModal;
    export let data_temp;

</script>

<main class="container">
    <h1>영화정보</h1>
    {#each data_temp as data}
    <div class="item">
      <figure>
        <img src={data.imgUrl} alt={data.title}>
      </figure>
      <div class="info">
        <h3 class="bg-yellow">{data.title}</h3>
        <p>개봉: {data.year}</p>
        <p>장르: {data.category}</p>
        <button on:click={() => {handleLike(data.id)}}>좋아요 {data.likeCount}</button>
        <button class="btn btn-primary" on:click={() => {openModal(data.id)}}>상세보기</button>
      </div>
    </div>
    {/each}
  </main>


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