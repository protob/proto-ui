<script setup lang="ts">
import { ref } from "vue";

const size = ref("");
const variant = ref<string>();
const passive = ref<string>();
const isRounded = ref(false);
const position = ref("right");
</script>

<template>
    <section>
        <o-field grouped>
            <o-switch v-model="isRounded" label="Rounded" />
            <o-switch
                v-model="position"
                true-value="left"
                false-value="right"
                label="Label on left" />
        </o-field>
        <o-field grouped>
            <o-field label="Variant">
                <o-select v-model="variant" expanded placeholder="Variant">
                    <option :value="undefined">Default</option>
                    <option value="primary">Primary</option>
                    <option value="secondary">Secondary</option>
                    <option value="success">Success</option>
                    <option value="info">Info</option>
                    <option value="warning">Warning</option>
                    <option value="danger">Danger</option>
                </o-select>
            </o-field>
            <o-field label="Passive Variant">
                <o-select
                    v-model="passive"
                    expanded
                    placeholder="Passive Variant">
                    <option :value="undefined">Default</option>
                    <option value="primary">Primary</option>
                    <option value="secondary">Secondary</option>
                    <option value="success">Success</option>
                    <option value="info">Info</option>
                    <option value="warning">Warning</option>
                    <option value="danger">Danger</option>
                </o-select>
            </o-field>
            <o-field label="Size">
                <o-select v-model="size" expanded>
                    <option value="">Default</option>
                    <option value="small">small</option>
                    <option value="medium">medium</option>
                    <option value="large">large</option>
                </o-select>
            </o-field>
        </o-field>

        <o-switch
            :rounded="isRounded"
            :position="position"
            :size="size"
            :variant="variant"
            :passive-variant="passive"
            label="Sample" />
    </section>
</template>
