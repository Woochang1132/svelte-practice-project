<script>
    export let movieData; // 영화 데이터를 받는다(props 변수 선언)
    export let selectedMovie; // 선택한 영화의 번호를 받는다.(props 변수 선언)
    export let closeModal; // 함수를 전달받음
</script>

<div class="modal">
    <div class="inner">
      <h3>{movieData[selectedMovie].title}</h3>
      <p>{@html movieData[selectedMovie].story}</p>
      <button class="btn-close" on:click={closeModal}>닫기</button>
    </div>
</div>

<style>
    .modal {
  background: rgba(0, 0 , 0, 0.7);
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal .inner{
  background: #fff;
  width: 80%;
  padding: 20px;
  border-radius: 10px;
}
</style>