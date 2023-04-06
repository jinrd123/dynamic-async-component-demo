<template>
    <div class="component-tab">
        <div class="tab">
            <div
                v-for="(value, key) in tabData"
                :key="key"
                :class="['tab-item', { 'active': currentTab == key }]"
                @click="switchTab(key)"
            >
                {{ value }}
            </div>
        </div>
        <div class="component">
            <component :is="currentComponent"></component>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, ref, defineAsyncComponent, computed } from 'vue'
import Intro from './Intro.vue';
const List = defineAsyncComponent(() => import("./List.vue"));
const Article = defineAsyncComponent(() => import("./Article.vue"));

export default defineComponent({
    name: "ComponentTab",
    components: {
        Intro,
    },
    setup () {
        const tabData = {
            'intro': 'Intro',
            'list': 'List',
            'article': 'Article'
        }
        const currentTab = ref('intro');
        const switchTab = (key: string) => {
            currentTab.value = key;
        }
        const currentComponent = computed(() => {
            switch(currentTab.value) {
                case 'intro': 
                    return Intro;
                case 'list':
                    return List;
                case 'article':
                    return Article;
            }
        })
        return {
            tabData,
            currentTab,
            switchTab,
            currentComponent
        }
    }
})
</script>

<style scoped lang="less">
.component-tab {
    width: 500px;
    height: 500px;
    border: 1px solid #000;
    margin: 0 auto;

    .tab {
        height: 50px;
        border-bottom: 1px solid #000;

        &-item {
            float: left;
            width: 33.33%;
            height: 50px;
            height: 100%;
            text-align: center;
            line-height: 50px;

            &.active {
                background-color: #000;
                color: #fff;
            }
        }
        
    }
}

.component {
    padding: 30px;
}

</style>