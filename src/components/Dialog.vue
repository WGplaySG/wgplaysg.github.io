<script setup lang="ts">
import { ref } from 'vue';

defineProps<{ title: string, msgs: string[] }>();

const active = ref(false);

const onButtonClick = () => active.value = true;
const onCloseClick = () => active.value = false;
</script>

<template>
    <section class="modal-container" :class="{ active }">
        <button class="modal-btn" @click="onButtonClick">点击我</button>
        <div class="modal-backdrop"></div>
        <div class="modal-content">
            <button class="modal-close" @click="onCloseClick">&#x2715;</button>
            <h2>{{ title }}</h2>
            <hr />
            <p v-for="(m, idx) in msgs" :key="idx">
                {{ m }}
            </p>
            <button class="modal-content-btn" @click="onCloseClick">好的</button>
        </div>
    </section>
</template>

<style scoped lang="less">
*,
*:before,
*:after {
    box-sizing: border-box;
}

body {
    height: 100vh;
    background: #fff;
    overflow: hidden;
}

button {
    border: none;
}

.modal-container {
    margin: 60px auto;
    padding-top: 0px;
    position: relative;
    width: 160px;

    .modal-btn {
        display: block;
        margin: 0 auto;
        color: #fff;
        width: 160px;
        height: 50px;
        line-height: 50px;
        background: #446CB3;
        font-size: 22px;
        border: 0;
        border-radius: 3px;
        cursor: pointer;
        text-align: center;
        box-shadow: 0 5px 5px -5px #333;
        transition: background 0.3s ease-in;

        &:hover {
            background: #365690;
        }
    }

    .modal-content,
    .modal-backdrop {
        height: 0;
        width: 0;
        opacity: 0;
        visibility: hidden;
        overflow: hidden;
        cursor: pointer;
        transition: opacity 0.2s ease-in;
    }

    .modal-close {
        color: #aaa;
        position: absolute;
        right: 5px;
        top: 5px;
        padding-top: 3px;
        background: #fff;
        font-size: 16px;
        width: 25px;
        height: 25px;
        font-weight: bold;
        text-align: center;
        cursor: pointer;

        &:hover {
            color: #333;
        }
    }

    .modal-content-btn {
        position: absolute;
        text-align: center;
        cursor: pointer;
        bottom: 20px;
        right: 30px;
        background: #446CB3;
        color: #fff;
        width: 50px;
        border-radius: 2px;
        font-size: 14px;
        height: 32px;
        line-height: 32px;
        font-weight: normal;

        &:hover {
            color: #fff;
            background: #365690;
        }
    }

    &.active .modal-backdrop {
        background-color: rgba(0, 0, 0, 0.6);
        width: 100vw;
        height: 100vh;
        position: fixed;
        left: 0;
        top: 0;
        z-index: 9;
        visibility: visible;
        opacity: 1;
        transition: opacity 0.2s ease-in;
    }

    &.active .modal-content {
        opacity: 1;
        background-color: #fff;
        max-width: 400px;
        width: 400px;
        height: 280px;
        padding: 10px 30px;
        position: fixed;
        left: calc(50% - 200px);
        top: 12%;
        border-radius: 4px;
        z-index: 999;
        pointer-events: auto;
        cursor: auto;
        visibility: visible;
        box-shadow: 0 3px 7px rgba(0, 0, 0, 0.6);

        @media (max-width: 400px) {
            left: 0;
        }
    }
}
</style>
