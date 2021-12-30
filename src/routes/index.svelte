<script>
import { Input } from "postcss";


    let tasks = []
    let addTask
    let newTask = ''; 
    let info = '';

    // add new task
    const addNewTask = () => {
        let taskItem = {id: new Date().getTime, task : newTask, isDone: false, date: new Date() } 
        tasks = [...tasks, taskItem];
    }
    

    const onKeyPress = event => {
        if(event.code == 'Enter') {
            if(newTask != ''){
                addNewTask()
                newTask = '';
                info = '';
            } else {
                info = 'new task is still empty ;)';
            }
        }
    }

    const removeTask = (index) => {
        tasks.splice(index, 1)
        tasks = tasks;
    }
    
</script>

<svelte:head>
    <title>Svelte Tailwindcss TodoApp</title>
</svelte:head>

<!-- todo container -->
<div class="container px-3 mx-auto">
    <!-- todo wrapper -->
    <div class="bg-white rounded shadow px-4 py-4" x-data="app()">
        <div class="title font-bold text-lg">Todo Application</div>
        <div class="flex items-center text-sm mt-2">
        <button on:click={addTask.focus()}>
        <svg class="w-3 h-3 mr-3 focus:outline-none" fill="none" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24" stroke="currentColor">
            <path d="M12 4v16m8-8H4"></path>
        </svg>
        </button>
        <span>Click to add task</span>
    </div>
    <input id="addTask" type="text" bind:this={addTask} bind:value="{newTask}" on:keypress="{onKeyPress}" placeholder="what is your plan for today" class=" rounded-sm shadow-sm px-4 py-2 border border-gray-200 w-full mt-4">
    <p class="text-xs text-red-400 pt-2">{info}</p>
    <!-- todo list -->
    <ul class="todo-list mt-4">
        {#each tasks as item, index}
             <!-- content here -->
             <li class="flex justify-between items-center mt-3">
                 <div class="flex items-center">
                 <input type="checkbox" name="" bind:checked={item.isDone}>
                 <div class="capitalize ml-3 text-sm font-semibold" class:line-through={item.isDone}>{item.task}</div>
                 </div>
                 <div>
                 <button on:click={() => removeTask(index)}>
                     <svg class=" w-4 h-4 text-gray-600 fill-current" fill="none" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24" stroke="currentColor">
                     <path d="M6 18L18 6M6 6l12 12"></path>
                     </svg>
                 </button>
                 </div>
             </li>
        {/each}

    </ul>
    </div>

    
</div>