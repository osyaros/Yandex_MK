<script>
    export let card = {}
</script>

<style>
    .card{
        width: 200px;
        height: 250px;
        font-family: "Montserrat", sans-serif;
    }
    .wrapper{
        width: 100%;
        height: 100%;
        background-color: grey;
        border-radius: 20px;
        padding: 10px;
    }
    .title{
        text-wrap: wrap;
        max-height: 50px;
    }
</style>

<div class="card">
    <div class="wrapper">
        <div class="title">
            {card.title}
        </div>
        <div class="desc_fields">
            <div class="date">
                {card.date}
            </div>
            <div class="categoty">
                <img src="./{card.type}.svg" alt="CategoryImage" width="40px" height="40px"/>
            </div>
        </div>
    </div>
</div>