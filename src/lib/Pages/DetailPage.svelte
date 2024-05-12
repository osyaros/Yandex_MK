<script>
    import back from '../../static/back.svg'
    import StatusButton from '../UI/StatusButton.svelte';
    import LocalStorage from "../../store/store.svelte"
    import { onMount } from 'svelte';

    let items = [];
    let newItem = { name: '', date_to: '', date_from:'', status:"", goal:"", tasks:[]};

    // Функция для получения данных из localStorage при монтировании компонента
    onMount(() => {
    const storedItems = localStorage.getItem('items');
    if (storedItems) {
        items = JSON.parse(storedItems);
    }
    });

    let data = {
        name: "Домашняя работа №1",
        date_to: "10.11.2012",
        date_from: "11.05.2025",
        status: "Выполнено",
        goal: "Написать доклад по истории",
        tasks: [
            {name: "1 task", completed: true},
            {name: "2 task", completed: false}
        ]
    }

    

    let status_color;
    function calculateStatus() {
        let checkedCount = data.tasks.reduce((accum, curr) => accum + Number(curr.completed), 0);
        if (checkedCount === 0) {
            data.status = "Не начато";
            status_color = "#FFFFFF"; 
        } else if (checkedCount === data.tasks.length) {
            data.status = "Выполнено";
            status_color = '#559D49';
        } else {
            data.status = "В процессе";
            status_color = "#EFCD78";
        }
    }

    $:calculateStatus(); // Initial calculation

    function updateTaskStatus(taskIndex) {
        data.tasks[taskIndex].completed = !data.tasks[taskIndex].completed;
        calculateStatus();
    }
    function updateTaskName(taskIndex, newName){
        data.tasks[taskIndex].name  = newName;
    }
</script>

<style>
    .detailpage {
        font-family: "Montserrat", sans-serif;
        width: 67.36vw; 
        height: 100vh;
        margin-top: 2.5vh;
        margin-left: 6.59vw;
        background: url("../../static/backcard.svg") no-repeat center/cover; 
        border-radius: 25px;
        border: #585858 6px solid;
        padding-left: 2vw;
        padding-top: 2.5vh;
        display: flex;
        flex-direction: column;
        row-gap: 2vh;
    }
    .tools{
        display: flex;
        justify-content: start;
        gap:1.5vw;
    }
    .description{
        display: flex;
        flex-direction: column;
        gap:1vh;
        font-size: 20px;
    }
    .name{
        width: 600px;
        text-wrap: wrap;
        font-size:48px;
        font-weight: 600;
    }
    .divider{
        border-top: 4px solid #585858;
        width: 40vw;
    }

    .date{
        display: flex;
        flex-direction: column;
    }
    .goal{
        font-size: 32px;
    }
    .goal span{
        font-weight: 600;
    }
    .plan{
        font-size: 32px;
        font-weight: 600;
    }
    .plan_task{
        font-size: 20px;
        font-weight: 400;
    }
</style>

<div class="detailpage">
   <div class="tools">
        <img src={back} alt="back_button" />
        <StatusButton status={data.status} status_color={status_color} />
    </div>

    <div class="description">
        <div class="name">
            <h1>
                {data.name}
            </h1>
        </div>
        <div class="date">
            <span>Создано: {data.date_from}</span>
            <span>Выполнить до: {data.date_to}</span>
        </div>
        <div class="divider"></div>
    </div>
    <div class="goal">
        <span>Цель: </span>{data.goal}
    </div>
    <div class="plan">
        <h1>План:</h1>
        {#each data.tasks as task, index}
            <div class="plan_task">
                <input type="checkbox" checked={task.completed} on:change={() => updateTaskStatus(index)}/>
                <input type="text" value={task.name} on:input={() => updateTaskName(index, task.name)}/>
            </div>
        {/each}
        <div class="add_button">
            <span>+ Новый пункт</span>
        </div>  
    </div> 
</div>