<template>
<!-- @click.self is using event modifier to restrict to click self only, nothing inside -->
    <div class="backdrop" @click.self="closeModal">
        <div class="modal" :class="{ sale: theme === 'sale'}">
            <!-- a slot was passed down from parent component -->
            <!-- default content will show when nothing is passed in from parent component as slot -->
            <slot>default content</slot>
            <div class="actions">
                <!-- rendering a name slot with name as links -->
                <slot name="links"></slot>
            </div>
        </div>
    </div>
</template>

<script>
export default{
    // registering props from parent component
    props:['theme'],
    methods:{
        closeModal(){
            // creating a emitter listened by parent element to close modal
            this.$emit('close')
        }
    }
}
</script>

<style>
    
    .modal{
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background: white;
        border-radius: 10px;
    }
    .backdrop{
        top: 0;
        position: fixed;
        background: rgba(0,0,0,0.5);
        width: 100%;
        height: 100%;
    }
    .modal h1{
        color: #03cfb4;
        border: none;
        padding: 0;
    }
    .modal p{
        font-style: normal;
    }
    .modal .actions{
        text-align: center;
        margin: 30px 0 10px 0;
    }
    .modal .actions a{
        padding: 8px;
        border: 1px solid #eee;
        border-radius: 4px;
        margin: 10px;
        color: #333;
        text-decoration: none;
    }
    .modal.sale{
        background: crimson;
        color: white;
    }
    .modal.sale h1{
        color: white;
    }
    .modal.sale .actions{
        color: white;
    }
    .modal.sale .actions a{
        color: white;
    }
</style>