<template>
    <div class="dropdown" ref="dropdown">
        <button class="dropdown__toggle" @click="toggleDropdown">
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 16 16" fill="none">
                <path
                    d="M9 5C9 5.55228 8.55228 6 8 6C7.44772 6 7 5.55228 7 5C7 4.44772 7.44772 4 8 4C8.55228 4 9 4.44772 9 5Z"
                    fill="#4AB4FF" />
                <path
                    d="M9 8C9 8.55228 8.55228 9 8 9C7.44772 9 7 8.55228 7 8C7 7.44772 7.44772 7 8 7C8.55228 7 9 7.44772 9 8Z"
                    fill="#4AB4FF" />
                <path
                    d="M9 11C9 11.5523 8.55228 12 8 12C7.44772 12 7 11.5523 7 11C7 10.4477 7.44772 10 8 10C8.55228 10 9 10.4477 9 11Z"
                    fill="#4AB4FF" />
            </svg>
        </button>
        <div v-if="isOpen" class="dropdown__menu" v-click-outside="closeDropdown">
            <slot></slot>
        </div>
    </div>
</template>
  

<script>
export default {
    data() {
        return {
            isOpen: false,
        };
    },
    mounted() {
        document.addEventListener("click", this.onClickOutside);
    },
    beforeUnmount() {
        document.removeEventListener("click", this.onClickOutside);
    },
    methods: {
        toggleDropdown() {
            this.isOpen = !this.isOpen;
        },
        onClickOutside(event) {
            if (!this.$refs.dropdown.contains(event.target)) {
                this.closeDropdown();
            }
        },
        closeDropdown() {
            this.isOpen = false;
        },
    },
};
</script>
  
<style>
.dropdown {
    position: relative;
    border-radius: 2px;
    border: 1px solid var(--blue-border);
    background-color: var(--black-back);
    width: 24px;
    height: 24px;
    display: flex;
    justify-content: center;
    align-items: center;
}

.dropdown__toggle {
    background-color: var(--black-back);
    border: none;
    border-radius: 4px;
    cursor: pointer;
    width: 100%;
    height: 100%;
}

.dropdown__menu {
    position: absolute;
    top: 100%;
    left: 0;
    border-radius: 4px;
    padding: 2px 0px;
    z-index: 9999;
    margin-top: 2px;
    background-color: var(--black-back);
}

.dropdown__menu>ul {
    box-shadow: 0px 0px 6px 0px rgba(0, 0, 0, 0.75);
    border-radius: 2px;
    width: 200px;
}

.dropdown__menu>ul>li {
    margin-bottom: 1px;
}

.dropdown__menu>ul>li>button {
    width: 100%;
    cursor: pointer;
    text-align: left;
    background-color: #212B41;
    padding: 6px 12px;
    color: var(--white);
    white-space: nowrap;
    font-size: 14px;
    line-height: 20px;
    letter-spacing: 0.252px;
    border: none;
}

.dropdown__menu>ul>li>button:hover {
    background-color: var(--gray-back);
}

.dropdown__menu>ul>li>button:disabled {
    background-color: #1B2436;
    color: #868F98;
    cursor: auto;
}

.dropdown__menu>ul>li>button:disabled:hover {
    background-color: #212B41;
}

</style>