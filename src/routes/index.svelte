<script>
    let tasks = [{task: "buy groceries", isDone:false, date: '2021-16-12'},
                   {task: "filling water", isDone:false, date: '2021-16-12'},
                   {task: "read a book", isDone:false, date: '2021-16-12'}
    ];

    let newTask = ''

    const addNewTask = () => {
        console.log(newTask);
    }

    const onKeyPress = event => {
        if(event.code == 'Enter') {
            
        }
    }

</script>

<!-- todo container -->
<div class="container px-3 max-w-md mx-auto">
    <!-- todo wrapper -->
    <div class="bg-white rounded shadow px-4 py-4" x-data="app()">
    <div class="title font-bold text-lg">Todo Application</div>
    <div class="flex items-center text-sm mt-2">
        <button>
        <svg class="w-3 h-3 mr-3 focus:outline-none" fill="none" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" viewBox="0 0 24 24" stroke="currentColor">
            <path d="M12 4v16m8-8H4"></path>
        </svg>
        </button>
        <span>Click to add task</span>
    </div>
    <input type="text" bind:value="{newTask}" on:keypress="{onKeyPress}" placeholder="what is your plan for today" class=" rounded-sm shadow-sm px-4 py-2 border border-gray-200 w-full mt-4">

    <!-- todo list -->
    <ul class="todo-list mt-4">
        {#each tasks as item}
             <!-- content here -->
             <li class="flex justify-between items-center mt-3">
                 <div class="flex items-center">
                 <input type="checkbox" name="" id="">
                 <div class="capitalize ml-3 text-sm font-semibold">{item.task}</div>
                 </div>
                 <div>
                 <button>
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