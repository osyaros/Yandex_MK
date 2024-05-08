<script>
  import Card from './lib/Components/Card.svelte';
  import CategoryBar from './lib/Components/CategoryBar.svelte';
  import Header from './lib/Components/Header.svelte';
  import DetailPage from './lib/Pages/DetailPage.svelte';
  let cards = [
        { title: 'Название 1', date: "22.04.23",type:"study"},
        { title: 'Название 2', date: "11.11.11", type:"home"},
        { title: 'Название 3', date: "3.1.15", type:"sport"}
    ];

    import LocalStorage from './store/store.svelte';
</script>

<main>
  <Header />
  <div class="main_block">
    <CategoryBar />
    <DetailPage />
    <div class="cards_place">
      <!-- {#each cards as card}
        <Card card = {card}/>
      {/each} -->
      
      <!-- <LocalStorage /> -->
      
    </div>
  </div>
</main>

<style>
  main{
    width: 100%;
  }
  .main_block{
    display: flex;
    flex-direction: row;
    justify-content: start;
  }
  .cards_place{
    padding-left: 50px;
    padding-top:  2.5vh;
    display: flex;
    flex-wrap: wrap;
    flex-direction: row;
    column-gap: 40px;
  }
</style>
