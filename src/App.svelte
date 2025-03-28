<script>
  import logo1 from './assets/svelte.svg'
  const datas = [
    {
      title: '고질라 X 콩: 뉴 엠파이어',
      year: 2024,
      category: '어드벤처, 액션, SF'
    },
    {
      title: '고질라 X 콩: 뉴 엠파이어',
      year: 2024,
      category: '어드벤처, 액션, SF'
    },
    {
      title: '듄 파트2',
      year: 2024,
      category: '액션'
    },
  ];
  let likeCount = 0;
  const handleLike = () => {
    likeCount += 1;
  }

</script>

<main>
  <h1>영화정보</h1>
  <img src={logo1} alt="">
  <img src="/vite.svg" alt="">
  {#each datas as data}
  <div>
    <h3 class="bg-yellow">{data.title}</h3>
    <p>개봉: {data.year}</p>
    <p>장르: {data.category}</p>
    <button on:click={handleLike}>좋아요 {likeCount}</button>
  </div>
  {/each}

</main>

<style>
.bg-yellow{
  background: gold;
  padding: 10px;
  color: #333;
}
</style>
