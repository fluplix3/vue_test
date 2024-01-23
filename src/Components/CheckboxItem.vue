<template>
    <label :class="checkboxClasses">
        <span class="checkbox__icon" tabindex="0">
            <svg v-if="isChecked" xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 16 16" fill="none">
                <path
                    d="M7.00002 12.4L3.30002 8.7C3.11746 8.51371 3.01579 8.2629 3.0171 8.00207C3.01842 7.74125 3.12262 7.49148 3.30705 7.30704C3.49149 7.1226 3.74126 7.0184 4.00209 7.01709C4.26292 7.01577 4.51373 7.11744 4.70002 7.3L7.00002 9.6L12.3 4.3C12.4863 4.11744 12.7371 4.01577 12.9979 4.01709C13.2588 4.0184 13.5085 4.1226 13.693 4.30704C13.8774 4.49148 13.9816 4.74125 13.9829 5.00207C13.9843 5.2629 13.8826 5.51371 13.7 5.7L7.00002 12.4Z"
                    fill="#4AB4FF" />
            </svg>
        </span>
        <input type="checkbox" @input="handleChange" :checked="isChecked" :disabled="disabled" />
        <span class="checkbox__label">
            <slot></slot>
        </span>
    </label>
</template>
  
<script>
export default {
    props: {
        disabled: {
            type: Boolean,
            default: false
        },
        modelValue: {
            type: Boolean,
            default: false
        }
    },
    computed: {
        isChecked: {
            get() {
                return this.modelValue;
            },
            set(value) {
                this.$emit('update:modelValue', value);
            }
        },
        checkboxClasses() {
            return {
                checkbox: true,
                'checkbox--checked': this.isChecked,
                'checkbox--disabled': this.disabled
            };
        }
    },
    methods: {
        handleChange(event) {
            this.isChecked = event.target.checked;
            this.$emit('input', this.isChecked);
        }
    }
};
</script>
  
<style scoped>
.checkbox {
    display: inline-flex;
    align-items: center;
    padding: 5px;
}

.checkbox--checked .checkbox__icon {
    background-color: #000;
}

.checkbox--disabled {
    opacity: 0.5;
    pointer-events: none;
}

.checkbox--disabled .checkbox__icon {
    border: 1px solid #3E517A;
}

.checkbox__label {
    font-size: 12px;
    font-style: normal;
    font-weight: 400;
    line-height: 16px;
    letter-spacing: 0.396px;
    color: #92A4C8;
}

.checkbox--checked .checkbox__label {
    color: var(--white);
}

.checkbox--checked, .checkbox--disabled .checkbox__label {
    color: #868F98;
}

.checkbox input[type="checkbox"] {
    display: none;
}

.checkbox__icon {
    width: 20px;
    height: 20px;
    border-radius: 4px;
    border: 1px solid var(--gray-back);
    background: var(--black-back);
    display: flex;
    justify-content: center;
    align-items: center;
    margin-right: 7px;
}

.checkbox__icon:focus {
    border: 1px solid var(--blue-border);
}

.checkbox--checked .checkbox__icon {
    background-color: var(--gray-back);
}
</style>