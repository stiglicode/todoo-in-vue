<script>
    export default {
        props: ["count"]
    }

</script>

<template>
	<div class="d-flex flex-row justify-content-center">
        <p>Task count:</p>
        <strong>&nbsp;{{ count }}&nbsp;</strong>
    </div>
    <hr/>
</template>

<style>

</style>
