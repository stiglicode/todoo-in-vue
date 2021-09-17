<script>
    export default {
        props: ["title", "status", "priority", "date"],
        methods: {
            removeHandler() {
                return this.$emit("removeItem", "dead")
            }
        }
    }
</script>
<template>
    <div :class="'todoo-item todoo-item-' + priority + ' ' + 'd-flex flex-row justify-content-between align-items-center'">
        <div class="d-flex flex-column justify-content-start">
            <h2 class="d-flex flex-wrap text-start">{{ title }}</h2>
            <span class="d-flex flex-wrap">Created at:&nbsp;<i>{{ date }}</i></span>
        </div>
        <div class="remove-btn">
            <button class="btn btn-outline-danger" @click="removeHandler" >×</button>
        </div>
    </div>
</template>

<style>
    
    .todoo-item {
        padding: 1rem;
        transition: background .2s ease;
        border-radius: .625rem;
        margin-bottom: 1rem;
    }

    .todoo-item:last-child {
        margin-bottom: 0;
    }

    .todoo-item:hover {
        background-color: rgba(0, 0, 0, .1);
    }

    .todoo-item:hover > .remove-btn {
        opacity: 1;
        pointer-events: all;
    }

    .remove-btn {
        opacity: 0;
        pointer-events: none;
        transition: opacity .2s ease;
    }

    .todoo-item-low {
        background-color: rgb(143, 228, 253);
    }

    .todoo-item-low:hover {
        color: rgb(50, 159, 189);
    }

    .todoo-item-med {
        background-color: rgb(253, 196, 143);
    }

    .todoo-item-med:hover {
        color: rgb(189, 124, 50);
    }

    .todoo-item-heigh {
        background-color: rgb(253, 143, 143);
    }

    .todoo-item-heigh:hover {
        color: rgb(189, 50, 50);
    }

</style>