<template>
    <DocComponent title="Vue Password Component" header="Password" description="Password displays strength indicator for password fields." :componentDocs="docs" :apiDocs="['Password']" />
</template>

<script>
import AccessibilityDoc from '@/doc/password/AccessibilityDoc.vue';
import BasicDoc from '@/doc/password/BasicDoc.vue';
import DisabledDoc from '@/doc/password/DisabledDoc.vue';
import FloatLabelDoc from '@/doc/password/FloatLabelDoc.vue';
import ImportDoc from '@/doc/password/ImportDoc.vue';
import InvalidDoc from '@/doc/password/InvalidDoc.vue';
import LocaleDoc from '@/doc/password/LocaleDoc.vue';
import MeterDoc from '@/doc/password/MeterDoc.vue';
import StyleDoc from '@/doc/password/StyleDoc.vue';
import TemplateDoc from '@/doc/password/TemplateDoc.vue';
import ToggleMaskDoc from '@/doc/password/ToggleMaskDoc.vue';
import VeeValidateDoc from '@/doc/password/form/VeeValidateDoc.vue';

export default {
    data() {
        return {
            docs: [
                {
                    id: 'import',
                    label: 'Import',
                    component: ImportDoc
                },
                {
                    id: 'basic',
                    label: 'Basic',
                    component: BasicDoc
                },
                {
                    id: 'meter',
                    label: 'Meter',
                    component: MeterDoc
                },
                {
                    id: 'locale',
                    label: 'Locale',
                    component: LocaleDoc
                },
                {
                    id: 'togglemask',
                    label: 'ToggleMask',
                    component: ToggleMaskDoc
                },
                {
                    id: 'template',
                    label: 'Template',
                    component: TemplateDoc
                },
                {
                    id: 'floatlabel',
                    label: 'FloatLabel',
                    component: FloatLabelDoc
                },
                {
                    id: 'invalid',
                    label: 'Invalid',
                    component: InvalidDoc
                },
                {
                    id: 'disabled',
                    label: 'Disabled',
                    component: DisabledDoc
                },
                {
                    id: 'form',
                    label: 'Form',
                    description: 'Compatibility with popular Vue form libraries.',
                    children: [
                        {
                            id: 'vee-validate',
                            label: 'Vee Validate',
                            component: VeeValidateDoc
                        }
                    ]
                },
                {
                    id: 'style',
                    label: 'Style',
                    component: StyleDoc
                },
                {
                    id: 'accessibility',
                    label: 'Accessibility',
                    component: AccessibilityDoc
                }
            ]
        };
    }
};
</script>
