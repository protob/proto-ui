<script setup lang="ts">
import { ref, useTemplateRef } from "vue";

const dropdownbtn = useTemplateRef<HTMLElement>("dropdownBtn");
const currentMenu = ref("");
const subitem = "dropdownitem";

const inspectData = [
    {
        class: "rootClass",
        description: "Class of the root element",
    },
    {
        class: "triggerClass",
        description: "Class of the trigger element",
    },
    {
        class: "teleportClass",
        description: "Class when the dropdown is teleported",
        properties: ["teleport"],
        action: (cmp, data) => {
            data.teleport = true;
            setTimeout(() => {
                dropdownbtn.value?.click();
            }, 300);
        },
    },
    {
        class: "menuMobileOverlayClass",
        description: "Class of the overlay when on mobile",
        warning: "Switch to mobile view to see it in action!",
        specificity: "when <b>mobileClass</b> is applied",
        action: () => {
            setTimeout(() => {
                dropdownbtn.value?.click();
            }, 300);
        },
    },
    {
        class: "menuClass",
        description: "Class of the dropdown menu",
        specificity:
            "when <b>inlineClass</b> or <b>mobileClass</b> or <b>expandedClass</b> is applied",
        action: () => {
            setTimeout(() => {
                dropdownbtn.value?.click();
            }, 300);
        },
    },
    {
        class: "disabledClass",
        description: "Class of dropdown when disabled",
        properties: ["disabled"],
        action: (cmp, data) => {
            data.disabled = true;
        },
    },
    {
        class: "menuActiveClass",
        description: "Class of dropdown menu when active",
        properties: ["inline", "active"],
        action: () => {
            setTimeout(() => {
                dropdownbtn.value?.click();
            }, 300);
        },
    },
    {
        class: "inlineClass",
        description: "Class of dropdown menu when inline",
        properties: ["inline"],
        action: (cmp, data) => {
            data.inline = true;
        },
    },
    {
        class: "menuPositionClass",
        description: "Class of dropdown menu position",
        properties: ["position"],
        suffixes: ["top-right", "top-left", "bottom-right", "bottom-left"],
        action: (cmp, data) => {
            data.position = "top-right";
            setTimeout(() => {
                dropdownbtn.value?.click();
            }, 300);
        },
    },
    {
        class: "mobileClass",
        description: "Class of dropdown when on mobile",
        warning: "Switch to mobile view to see it in action!",
        action: () => {
            setTimeout(() => {
                dropdownbtn.value?.click();
            }, 300);
        },
    },
    {
        class: "expandedClass",
        description: "Class of dropdown when expanded",
        properties: ["expanded"],
        action: (cmp, data) => {
            data.expanded = true;
        },
    },
    {
        class: "itemClass",
        description: "Class of the dropdown item",
        subitem: true,
        action: () => {
            setTimeout(() => {
                dropdownbtn.value?.click();
            }, 300);
        },
    },
    {
        class: "itemActiveClass",
        description: "Class of the dropdown item when active",
        subitem: true,
        action: () => {
            setTimeout(() => {
                dropdownbtn.value?.click();
            }, 300);
        },
    },
    {
        class: "itemDisabledClass",
        subitem: true,
        description: "Class of the dropdown item when disabled",
        properties: ["disabled"],
        action: () => {
            setTimeout(() => {
                dropdownbtn.value?.click();
            }, 300);
        },
    },
    {
        class: "itemClickableClass",
        subitem: true,
        description: "Class of the dropdown item when clickable",
        properties: ["clickable"],
        action: () => {
            setTimeout(() => {
                dropdownbtn.value?.click();
            }, 300);
        },
    },
];
</script>

<template>
    <inspector-wrapper
        v-slot="props"
        :inspect-data="inspectData"
        :subitem="subitem">
        <o-dropdown v-model="currentMenu" v-bind="props">
            <template #trigger="{ active }">
                <o-button
                    ref="dropdownBtn"
                    label="Click me!"
                    variant="primary"
                    :icon-right="active ? 'caret-up' : 'caret-down'" />
            </template>
            <o-dropdown-item v-bind="props" value="ac1">
                Action
            </o-dropdown-item>
            <o-dropdown-item v-bind="props" value="ac2">
                Another action
            </o-dropdown-item>
            <o-dropdown-item v-bind="props" value="ac3" disabled>
                Something else
            </o-dropdown-item>
        </o-dropdown>
    </inspector-wrapper>
</template>
