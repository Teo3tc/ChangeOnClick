<script>
  let save = [];
  const chekckArray = (array, el) => array.filter(a => a.id == el);
  const newt = [
    { id: 0, color: "blue" },
    { id: 1, color: "green" },
    { id: 2, color: "red" },
    { id: 3, color: "black" }
  ];

  const handleClick = e => {
    const id = e.target.getAttribute("id");
    const findColor = chekckArray(newt, id);
    console.log(findColor);

    save = {
      color: findColor[0].color
    };
    return console.log(save);
  };
  $: console.log(save.color);
</script>

<style>
  .box {
    width: 100vw;
    height: 100vh;
    background-color: rgba(0, 0, 0, 0.3);
    display: grid;
    grid-template-columns: repeat(5, 20%);
    grid-template-rows: repeat(5, 20%);
  }
  .box_back_img {
    grid-area: 1/1/-1/-1;
    background: blue;
    transition: all 0.8s ease-in-out;
  }
  .box_btn {
    grid-area: 5/1/-1/-1;
    background: gray;
    display: flex;
    justify-content: space-evenly;
    align-items: center;
  }
  .btn {
    width: 100px;
    height: 100px;
    background-color: aquamarine;
  }
</style>

<main>
  <div class="box">
    <div class="box_back_img" style="background:{save.color}">
      <div class="text_desc" />
    </div>
    <div class="box_btn">
      {#each newt as { id }}
        <div class="btn" on:click={handleClick} {id} />
      {/each}
    </div>
  </div>
</main>
