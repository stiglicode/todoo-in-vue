<template>
   <div class="row justify-content-center new-task py-5 mt-5">
        <div class="col-6">
            <form @submit.prevent="submitHandler">
                <div class="d-flex flex-column align-items-start">
                    <label for="taskTitle" class="form-label">To doo name</label>
                    <input type="text" class="form-control" id="taskTitle" v-model="task_title">
                </div>
                <div class="d-flex flex-row align-items-center justify-content-start mt-3">
                    <input type="radio" class="form-check-input mt-0"  name="r-priority" id="r-low" @input="radioHandler">
                    <label class="form-check-label ms-2" for="r-low">Low priority</label>
                </div>
                <div class="d-flex flex-row align-items-center justify-content-start">
                    <input type="radio" class="form-check-input mt-0"  name="r-priority" id="r-med" @input="radioHandler">
                    <label class="form-check-label ms-2" for="r-med">Medium priority</label>
                </div>
                <div class="d-flex flex-row align-items-center justify-content-start">
                    <input type="radio" class="form-check-input mt-0"  name="r-priority" id="r-heigh" @input="radioHandler">
                    <label class="form-check-label ms-2" for="r-heigh">Height priority</label>
                </div>
                <button type="submit" class="btn btn-success w-100 mt-2">Save</button>
            </form>
        </div>
    </div>
</template>
<script>
export default {
    name: "NewTodo",
    data() {
        return {
            task_title: '',
            task_priority: '',
            task_date: ''
        }
    },
    methods:{
        submitHandler() {
            const date = new Date();
            this.task_date = `${date.getDay()}. ${date.getMonth()}. ${date.getFullYear()}`;
            this.$emit("taskItem", {
						title: this.task_title,
						status: "alive",
						priority: this.task_priority,
						created_at: this.task_date
            })
            this.task_title = '';
        },

        radioHandler(e) {
            return this.task_priority = e.currentTarget.id.split("-")[1];
        }
    }
}
</script>
<style>
   .new-task {
      background-color: rgb(230, 246, 255);
   }
</style>