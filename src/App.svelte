<script>
  import logo1 from './assets/svelte.svg'
  let title = '영화제목2'
  let year = 2024
  let category = '액션'
  let textRed = "color: red;"

  const datas = [
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
  ]

  const foods = ['pizza', 'burger', 'sushi', 'pasta'];
</script>

<main>
  {#each foods as food, i}
    <p>{i}: {food}</p>
  {/each}
  <h1>영화정보</h1>
  <img src={logo1} alt="">
  <img src="/vite.svg" alt="">
  {#each datas as data}
  <div>
    <h3 class="bg-yellow" style={textRed}>{data.title}</h3>
    <p>개봉: {data.year}</p>
    <p>장르: {data.category}</p>
  </div>
  {/each}

</main>

<style>
.bg-yellow{
  background: gold;
}
</style>
