<template>
    <div class="container">
        <p>Часть 1</p>
        <div class="container__chapter1 chapter-styles">
            <CheckboxList  />
            <p class="container__chapter1-license">
                Я принимаю <a href="#">лицензионное соглашение</a>
                <CheckboxItem v-model="licenseAgreementAccepted" />
            </p>
        </div>
        <p>Часть 2</p>
        <div class="container__chapter2 chapter-styles">
            <DropdownMenu>
                <ul>
                    <li><button>Элемент 1</button></li>
                    <li><button>Элемент 2</button></li>
                    <li><button>Элемент 3</button></li>
                    <li><button disabled>Элемент 4</button></li>
                </ul>
            </DropdownMenu>
        </div>
    </div>
</template>
  
<script>
import CheckboxList from './Components/CheckboxList.vue';
import CheckboxItem from './Components/CheckboxItem.vue';
import DropdownMenu from './Components/DropdownMenu.vue';

export default {
    components: {
        CheckboxList,
        CheckboxItem,
        DropdownMenu
    },
    data() {
        return {
            licenseAgreementAccepted: false
        };
    }
};
</script>

<style>
@font-face {
    font-family: "Gotham Pro";
    src: local("Gotham"),
        url('./fonts/GothamProNarrow-Medium.woff2') format("woff2"),
        url('./fonts/GothamProNarrow-Medium.woff') format("woff");
}

:root {
    --white: white;
    --gray-back: #303F5F;
    --black-back: #151B29;
    --blue-border: #4AB4FF;
}

* {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    font-family: "Gotham Pro";
}

ul {
    list-style: none;
}

.container {
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    background-color: #0E121B;
}

.container>p {
    font-size: 24px;
    color: var(--white);
}

.chapter-styles {
    padding: 30px;
    border: 2px dashed var(--blue-border);
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.container__chapter1-license {
    color: var(--white);
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 20px;
}

.container__chapter1-license>a {
    margin-left: 5px;
}

.container__chapter1-selected,
.container__chapter1-selected-element {
    color: var(--white);
}
</style>