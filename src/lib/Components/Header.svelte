<script>
    import yandexLogo from '../../static/yandexLogo.svg'
    import museumLogo from '../../static/museumLogo.svg'
    import ProgressBar from '../UI/ProgressBar.svelte';
    let total_task = 100;
    let total_done = 2;
</script>

<style>
   .header{
    font-family: "Montserrat", sans-serif;
    font-weight: 600;
    display: flex;
    background-color: #171717;
    width: 100%;
    height: 8vh;
    min-height: 80px;
    align-items: center;
    justify-content: space-between;
    max-height: 80px;
   }
   .left_side{
    display: flex;
    width: 10vw;
    height: 100%;
    justify-content: center;
    align-items: center;
    gap:0.5vw;
    min-width: 80px;
   } 
   .yandexLogo{
    width: 2vw;
    height: 2vw;
    min-height: 20px;
    min-width: 20px;
   }
   .museumLogo{
    height: 2vw;
    width: auto;
    min-width: 60px;
    min-height: 20px;
   }
   .right_side{
    display: flex;
    flex-direction: row;
    margin-right: 5vw;
    gap:1vw;
    align-items: center;
    overflow: hidden;
   }
   .total{
    font-size:15px;
    display: flex;
    flex-direction: row;
    width:60px ;
    height: 60px;
    
   }
</style>

<!-- markup (zero or more items) goes here -->
<div class='header'>
    <div class='left_side'>
        <img src={yandexLogo} class="yandexLogo" alt="YandexLogo" width="38px" height="38px"/>
        <img src={museumLogo} class="museumLogo" alt="YandexMuseumLogo" width="110px" style="margin-top: 2px;" />
    </div>
    <div class='right_side'>
        <span>Сделано</span>
        <div class ='total'>
            <ProgressBar max="{total_task}" value ="{total_done}" />
        </div>
    </div>
</div>