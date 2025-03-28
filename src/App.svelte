<script>
  import logo1 from './assets/svelte.svg'
  const datas = [
    {
      title: '파묘',
      year: 2024,
      category: '어드벤처, 액션, SF',
      likeCount: 0,
      imgUrl : '/images/파묘.jpg'
    },
    {
      title: '고질라 X 콩: 뉴 엠파이어',
      year: 2024,
      category: '어드벤처, 액션, SF',
      likeCount: 0,
      imgUrl : '/images/고질라X콩.jpg'
    },
    {
      title: '듄 파트2',
      year: 2024,
      category: '액션',
      likeCount: 0,
      imgUrl : '/images/듄-파트2.jpg'
    },
  ];
  const handleLike = (i) => {
    datas[i].likeCount += 1;
  }

</script>

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
