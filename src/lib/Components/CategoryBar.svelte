<script>
    import home from '../../static/home.svg'
    import sport from '../../static/sport.svg'
    import study from '../../static/study.svg'

    let categories = [
        { name: 'Все', selected: true, image:""},
        { name: 'Учеба', selected: false, image: study},
        { name: 'Домашние дела', selected: false, image:home },
        { name: 'Спорт', selected: false, image:sport}
    ];

    function selectCategory(index) {
        categories = categories.map((category, i) => ({
            ...category,
            selected: i === index
        }));
    }
</script>

<style>
    .categorybar {
        display: flex;
        flex-direction: column;
        /* background-color: #1C1C1C; */
        height: 100vh;
        width: 18vw;
        min-width: 80px;
        font-family: "Montserrat", sans-serif;
        max-width: 10vw; /* Limit the width to prevent overflow */
        overflow-x: hidden; /* Hide horizontal overflow */
        gap: 4vh;
        padding-top:  2.5vh;
    }

    .category {
        display: flex;
        flex-direction: row;
        justify-content: end;
        align-items: center;
        width: 10vw;
        height: 50px;
        cursor: pointer;
        -webkit-transition: background-color 0.4s;
        transition: background-color 0.4s;
        font-weight: 500;
        font-size:18px;
        border-radius: 0 50px 50px 0;
        gap:3px;
        padding-right: 1vw;
        -webkit-transition: width ease-in-out 0.8s;
        transition: ease-in-out 0.8s;
    }
    .category:hover{
        transition: 0.15s;
        border: none;
    }
    img {
        width: 2vw;
        min-width: 2vw;
    }
    @media only screen and (min-width: 700px) and (max-width:1060px) {
        span{
            font-size: 1.6vw;
        }
    }
    @media only screen and (min-width: 250px) and (max-width:700px) {
        span{
            display: none;
        }
        
}
</style>

<div class="categorybar">
    {#each categories as category, index}
        <button class="category" style="background-color: {category.selected ? '#559D49' : 'grey'}; width:{category.selected ? '100%':'7vw'}" on:click={() => selectCategory(index)}>
            {#if category.image}
                <span style="display:{category.selected ? '':'none'}">{category.name}</span>
                <img src={category.image} alt="CategoryImage" />
            {:else}
                <span>{category.name}</span>
            {/if}
            
        </button>
    {/each}
</div>
