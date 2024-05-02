<script>
 import { onMount } from 'svelte';

 let items = [];
 let newItem = { name: '', description: '' };

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
    newItem = { name: '', description: '' };
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