<script>
    export let note
    export let id

    import { db } from "../configs/firestore";

    const deleteNote = () => {
        db.collection('notes').doc(id).delete()
    }

    const updateNote = () => {
        db.collection('notes').doc(id).update({
            'title': note.title,
            'desc': note.desc
        })
    }
</script>

<div class="note" id="note">
    <input type="text" bind:value={note.title}>
    <textarea cols="10" rows="5" bind:value={note.desc}></textarea>
    <div class="actions">
        <button on:click={updateNote}>🔄</button>
        <button on:click={deleteNote}>🗑</button>
    </div>
</div>

<style>
    .note{
        border-radius: 5px;
        border: 1px solid #aaa;
        padding: 5px 8px;
        box-shadow: 0px 2px 3px rgba(0,0,0,.1);
        display: grid;
        width: 600px;
        overflow: hidden;
    }

    .note:not(:first-child){
        margin-top: 8px;
    }

    .note:last-child{
        margin-bottom: 15px;
    }

    .top input{
        width: 560px;
    }

    button{
        cursor: pointer;
    }
</style>