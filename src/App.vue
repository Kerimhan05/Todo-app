<template>
    <div class="wrapper">
        <main class="main">
            <div class="todo">
                <div class="container">
                    <div class="todo__body">
                        <div class="todo__title">
                            ToDo App
                        </div>
                        <div class="create">
                            <div class="create__title">
                                <label for="input__create">
                                                        New ToDo
                                            </label>
                            </div>
                            <div class="create__input">
                                <input v-bind:class='{control: required}' v-model="todo" type="text" required id="input__create text" v-bind:title="message">
                            </div>
                            <div class="create__button">
                                <button @keydown.enter="addTodo" @click="addTodo" class="btn__add">
                                                        Add ToDo
                                        </button>
                            </div>
                        </div>
                        <div class="todo__list">
                            <div class="todo__list-title">
                                ToDo List
                            </div>
                            <div class="list__items">
                                <div v-for="i in items" :key="i" class="list__item">
                                    <div class="item__title" v-bind:class='{delete__accomplished: i.isRemove}'>
                                        {{ i.case}}
                                    </div>
                                    <div class="item__action">
                                        <div class="item__done">
                                            <input type="checkbox" v-model="i.isRemove">
                                        </div>
                                        <div class="item__button">
                                            <button class="item__btn" @click="deleteItem(i)">
                                                                Remove
                                                        </button>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div v-if="items.length === 0" class="empty__list">
                            Empty List
                        </div>
                    </div>
                </div>
            </div>
        </main>
    </div>
</template>

<script>
export default {
    data() {
        return {
            todo: null,
            items: [],
            remove: false,
            message: 'Заполните поле',
            required: false
        };
    },
    methods: {
        addTodo() {
            const newItem = {
                case: this.todo,
                isRemove: this.remove,
            };
            if (this.todo !== null) {
                this.items.push(newItem);
                this.todo = null;
                this.required = false
            } else {
                this.required = true
            }
        },
        deleteItem(DeleteItem) {
            this.items = this.items.filter(i => i !== DeleteItem)
        },
    },
}
</script>

<style src="@/css/style.min.css">

</style>