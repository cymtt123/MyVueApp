<template>
    <form @submit.prevent="onsubmit">
        <h2 class="label-wrapper">
            <label for="new-todo-input" class="label__lg">
                What needs to be done?
            </label>
        </h2>
        <!-- .trim 相当于调用了trim()字符串方法 -->
        <!-- 如果不加.lazy则Vue会在键盘的每次输入事件（input事件）后就同步v-model的值，.lazy改成触发change事件后才同步 -->
        <input 
            type="text" 
            id="new-todo-input" 
            name="new-todo" 
            autocomplete="off" 
            v-model.lazy.trim="label" 
            class="input__lg"
        />
        <button type="submit" class="btn btn__primary btn__lg">Add</button>
    </form>
</template>

<script>
export default {
    methods:{
        onsubmit(){
            if(this.label===''){
                return;
            }
            this.$emit("todo-added", this.label);
            this.label = '';
        }
    },

    data(){
        return {
            label:""
        }
    }
}
</script>