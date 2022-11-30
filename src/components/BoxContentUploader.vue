<script setup>
    import { onMounted, onUnmounted } from 'vue'
    import '../../node_modules/box-ui-elements/dist/uploader.js'
    import '../../node_modules/box-ui-elements/dist/uploader.css'

    const props = defineProps({
        folderId: String
    })

    const contentUploader = new Box.ContentUploader();

    onMounted(() => {
        const accessToken = import.meta.env.VITE_BOX_DEVELOPER_TOKEN;
        contentUploader.show(props.folderId, accessToken, {
            container: '#box-content-uploader'
        });
    })

    onUnmounted(() => {
        contentUploader.hide();
    })
</script>

<template>
    <div id="box-content-uploader"></div>
</template>