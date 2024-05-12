<script>
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

 // Функция для добавления нового элемента
 function addItem() {
    items = [...items, newItem];
    localStorage.setItem('items', JSON.stringify(items));
    newItem = { name: '', date_to: '', date_from:'', status:"", goal:"", tasks:[]};
 }

 // Функция для удаления элемента по индексу
 function removeItem(index) {
    items = items.filter((_, i) => i !== index);
    localStorage.setItem('items', JSON.stringify(items));
 }
</script>

<div>
 <h2>Добавить новый элемент</h2>
 <input type="text" bind:value={newItem.name} placeholder="Название" />
 <input type="text" bind:value={newItem.description} placeholder="Описание" />
 <button on:click={addItem}>Добавить</button>
</div>

<div>
 <h2>Список элементов</h2>
 <ul>
    {#each items as item, index}
      <li>
        <span>{item.name} - {item.description}</span>
        <button on:click={() => removeItem(index)}>Удалить</button>
      </li>
    {/each}
 </ul>
</div>

<!-- let data = {
    name: "Домашняя работа №1",
    date_to: "10.11.2012",
    date_from:"11.05.2025",
    status: "Выполнено",
    goal: "Написать доклад по истории ",
    tasks: ["1 task", "2 task"],
    }
    -->