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
        background-color: #1C1C1C;
        height: 100vh;
        width: 10vw;
        min-width: 80px;
        font-family: "Montserrat", sans-serif;
        max-width: 10vw; /* Limit the width to prevent overflow */
        overflow-x: hidden; /* Hide horizontal overflow */
        
    }

    .category {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        width: 100%;
        height: 100px;
        cursor: pointer;
        transition: background-color 0.4s;
        font-weight: 500;
        font-size:18px;
        border:none;
    }
    .category:hover{
        color:#1d69fc;
        transition: 0.15s;
        border: none;
    }
    img {
        width: 40px;
    }
    @media only screen and (min-width: 700px) and (max-width:1060px) {
        span{
            font-size: 1.6vw;
        }
    }
    @media only screen and (min-width: 250px) and (max-width:700px) {
        span{
            display: none   ;
        }
        
}
</style>

<div class="categorybar">
    {#each categories as category, index}
        <button class="category" style="background-color: {category.selected ? 'grey' : 'transparent'}; border:none;" on:click={() => selectCategory(index)}>
            {#if category.image}
                <img src={category.image} alt="CategoryImage"/>
            {/if}
            <span>{category.name}</span>
        </button>
    {/each}
</div>