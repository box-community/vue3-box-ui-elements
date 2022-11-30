<template>
    <div id="box-content-explorer"></div>
</template>

<script setup>
    import { onMounted, onUnmounted } from 'vue'
    import '../../node_modules/box-ui-elements/dist/explorer.js'
    import '../../node_modules/box-ui-elements/dist/explorer.css'

    const props = defineProps({
        folderId: String
    })

    const contentExplorer = new Box.ContentExplorer();

    onMounted(() => {
        const accessToken = import.meta.env.VITE_BOX_DEVELOPER_TOKEN;
        contentExplorer.show(props.folderId, accessToken, {
            container: '#box-content-explorer'
        });
    })

    onUnmounted(() => {
        contentExplorer.hide();
    })
</script>