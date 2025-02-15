<template>
    <DocSectionText v-bind="$attrs">
        <p><a href="https://vee-validate.logaretm.com/v4/">VeeValidate</a> is a popular library for handling forms in Vue.</p>
    </DocSectionText>
    <div class="card flex justify-content-center">
        <form @submit="onSubmit" class="flex flex-column align-items-center gap-2">
            <ToggleButton v-model="value" :class="{ 'p-invalid': errorMessage }" aria-describedby="text-error" />
            <small id="text-error" class="p-error my-2">{{ errorMessage || '&nbsp;' }}</small>
            <Button type="submit" label="Submit" />
        </form>
    </div>
    <DocSectionCode :code="code" :dependencies="{ 'vee-validate': '4.8.2' }" />
</template>

<script>
import { useToast } from 'primevue/usetoast';
import { useField, useForm } from 'vee-validate';
export default {
    setup() {
        const { handleSubmit, resetForm } = useForm();
        const { value, errorMessage } = useField('value', validateField);
        const toast = useToast();

        function validateField(value) {
            if (!value) {
                return 'Value is required.';
            }

            return true;
        }

        const onSubmit = handleSubmit((values) => {
            if (values.value) {
                toast.add({ severity: 'info', summary: 'Form Submitted', detail: 'The form is successfully submitted.', life: 3000 });
                resetForm();
            }
        });

        return { value, handleSubmit, onSubmit, errorMessage };
    },
    data() {
        return {
            nodes: null,
            code: {
                basic: `
<div class="card flex justify-content-center">
    <form @submit="onSubmit" class="flex flex-column align-items-center gap-2">
        <ToggleButton v-model="value" :class="{ 'p-invalid': errorMessage }" aria-describedby="text-error" />
        <small id="text-error" class="p-error my-2">{{ errorMessage || '&nbsp;' }}</small>
        <Button type="submit" label="Submit" />
    </form>
</div>`,
                options: `
<template>
    <div class="card flex justify-content-center">
        <form @submit="onSubmit" class="flex flex-column align-items-center gap-2">
            <ToggleButton v-model="value" :class="{ 'p-invalid': errorMessage }" aria-describedby="text-error" />
            <small id="text-error" class="p-error my-2">{{ errorMessage || '&nbsp;' }}</small>
            <Button type="submit" label="Submit" />
        </form>
        <Toast />
    </div>
</template>

<script>
import { useToast } from 'primevue/usetoast';
import { useField, useForm } from 'vee-validate';
export default {
    setup() {
        const { handleSubmit, resetForm } = useForm();
        const { value, errorMessage } = useField('value', validateField);
        
        const toast = useToast();

        function validateField(value) {
            if (!value) {
                return 'Value is required.';
            }

            return true;
        }

        const onSubmit = handleSubmit((values) => {
            if (values.value) {
                toast.add({ severity: 'info', summary: 'Form Submitted', detail: 'The form is successfully submitted.', life: 3000 });
                resetForm();
            }
        });

        return { value, handleSubmit, onSubmit, errorMessage };
    },
};
<\/script>`,
                composition: `
<template>
    <div class="card flex justify-content-center">
        <form @submit="onSubmit" class="flex flex-column align-items-center gap-2">
            <ToggleButton v-model="value" :class="{ 'p-invalid': errorMessage }" aria-describedby="text-error" />
            <small id="text-error" class="p-error my-2">{{ errorMessage || '&nbsp;' }}</small>
            <Button type="submit" label="Submit" />
        </form>
        <Toast />
    </div>
</template>

<script setup>
import { useToast } from 'primevue/usetoast';
import { useField, useForm } from 'vee-validate';

const { handleSubmit, resetForm } = useForm();
const { value, errorMessage } = useField('value', validateField);
const toast = useToast();

function validateField(value) {
    if (!value) {
        return 'Value is required.';
    }

    return true;
}

const onSubmit = handleSubmit((values) => {
    if (values.value) {
        toast.add({ severity: 'info', summary: 'Form Submitted', detail: 'The form is successfully submitted.', life: 3000 });
        resetForm();
    }
});
<\/script>`
            }
        };
    }
};
</script>
