<svelte:head>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@400;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined" />
</svelte:head>

<script>
    import { onMount } from "svelte";

    export let counter = 0;

    function incrementa(){counter++}
    function decrementa(){if(counter > 0) counter--}
    function reset(){counter = 0}
    function save(){sessionStorage.setItem("counter", counter)}

    onMount(() => {
        const saved = sessionStorage.getItem("counter");
        if(saved !== null) counter = parseInt(counter, 10)
    });
</script>

<div class="main-container">
    <h1>Counter di sushi</h1>
    
    <div class="contanier">
        <div class="pulsante">
            <button on:click={reset}>
                <span class="material-symbols-outlined icon">refresh</span>
            </button>
        </div>

        <div class="pulsante">
            <button on:click={decrementa}>
                <span class="material-symbols-outlined icon">remove</span>
            </button>
        </div>

        <div class="number">
            {counter}
        </div>

        <div class="pulsante">
            <button on:click={incrementa}>
                <span class="material-symbols-outlined icon">add</span>
            </button>
        </div>

        <div class="pulsante">
            <button on:click={save}>
                <span class="material-symbols-outlined icon">save</span>
            </button>
        </div>
    </div>
</div>

<style>
    :global(body) {
        margin: 0;
        padding: 0;
        min-height: 100vh;
        font-family: 'Noto Sans JP', sans-serif;
    }
    
    .main-container {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        padding: 2rem;
    }
    
    h1 {
        color: #8b4513;
        font-size: 2.5rem;
        font-weight: 700;
        text-align: center;
        margin-bottom: 2rem;
        text-shadow: 2px 2px 4px rgba(205, 92, 92, 0.3);
        position: relative;
    }
    
    h1::after {
        content: '🍣';
        margin-left: 0.1rem;
        font-size: 2rem;
    }
    
    .contanier {
        display: flex;
        align-items: center;
        gap: 2rem;
        background: #ffffff;
        padding: 2rem 3rem;
        border-radius: 20px;
        box-shadow: 
            0 8px 32px rgba(139, 69, 19, 0.2),
            inset 0 2px 4px rgba(255, 255, 255, 0.8);
        border: 3px solid #cd5c5c;
        position: relative;
    }
    
    .contanier::before {
        content: '';
        position: absolute;
        top: -8px;
        left: -8px;
        right: -8px;
        bottom: -8px;
        background: linear-gradient(45deg, #8b4513, #cd5c5c, #8b4513);
        border-radius: 25px;
        z-index: -1;
        opacity: 0.3;
    }
    
    .pulsante button {
        width: 60px;
        height: 60px;
        border: none;
        border-radius: 50%;
        background: linear-gradient(145deg, #cd5c5c, #a0522d);
        color: #f8f5f0;
        cursor: pointer;
        display: flex;
        align-items: center;
        justify-content: center;
        transition: all 0.3s ease;
        box-shadow: 
            0 4px 15px rgba(139, 69, 19, 0.3),
            inset 0 2px 4px rgba(255, 255, 255, 0.2);
        position: relative;
        overflow: hidden;
    }
    
    .pulsante button::before {
        content: '';
        position: absolute;
        top: 0;
        left: -100%;
        width: 100%;
        height: 100%;
        background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.4), transparent);
        transition: left 0.5s;
    }
    
    .pulsante button:hover::before {
        left: 100%;
    }
    
    .pulsante button:hover {
        transform: translateY(-2px) scale(1.05);
        box-shadow: 
            0 6px 20px rgba(139, 69, 19, 0.4),
            inset 0 2px 4px rgba(255, 255, 255, 0.3);
    }
    
    .pulsante button:active {
        transform: translateY(0) scale(0.95);
        box-shadow: 
            0 2px 10px rgba(139, 69, 19, 0.3),
            inset 0 4px 8px rgba(0, 0, 0, 0.2);
    }
    
    .icon {
        font-size: 24px;
        font-weight: bold;
        text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
    }
    
    .number {
        display: flex;
        align-items: center;
        justify-content: center;
        min-width: 100px;
        height: 80px;
        font-size: 3rem;
        font-weight: 700;
        color: #8b4513;
        background: radial-gradient(circle, #f8f5f0 0%, #e8ddd4 100%);
        border-radius: 15px;
        border: 2px solid #8b4513;
        box-shadow: inset 0 4px 8px rgba(139, 69, 19, 0.1);
        position: relative;
        text-shadow: 2px 2px 4px rgba(205, 92, 92, 0.3);
    }
</style>