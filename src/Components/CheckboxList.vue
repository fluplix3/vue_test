<template>
    <div class="CheckboxList">
        <CheckboxItem v-for="item in checkboxItems" :key="item.id" v-model="item.checked" :disabled="item.disabled">
            {{ item.title }}
        </CheckboxItem>
        <p class="CheckboxList__selected">
            Выбранные элементы:
        </p>
        <ul>
            <li class="CheckboxList__selected-element" v-for="item in selectedItems" :key="item">{{ item }}
            </li>
        </ul>
    </div>
</template>
  
<script>
import CheckboxItem from './CheckboxItem.vue';

export default {
    components: {
        CheckboxItem
    },
    data() {
        return {
            checkboxItems: [
                {
                    id: 1,
                    title: 'apple',
                    visible: true,
                    disabled: true,
                    checked: false
                },
                {
                    id: 2,
                    title: 'melon',
                    visible: false,
                    checked: false
                },
                {
                    id: 3,
                    title: 'pineapple',
                    visible: true,
                    checked: false
                },
                {
                    id: 4,
                    title: 'watermelon',
                    visible: true,
                    checked: true,
                    disabled: true
                }
            ]
        };
    },
    computed: {
        selectedItems() {
            return this.checkboxItems.filter(item => item.checked).map(item => item.title);
        }
    }
};
</script>

<style>
.CheckboxList,
.CheckboxList>ul {
    display: flex;
    flex-direction: column;
    justify-content: center;
}

.CheckboxList>ul {
    align-items: center;
}

.CheckboxList__selected {
    font-size: 14px;
}

.CheckboxList__selected,
.CheckboxList__selected-element {
    color: var(--white);
}
</style>