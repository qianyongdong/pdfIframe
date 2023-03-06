<script setup>
import { ref } from "vue";
// import HelloWorld from "./components/HelloWorld.vue";
const urls = [
  {
    url: "/1.pdf",
    name: "1",
  },
  { url: "/2.pdf", name: "2" },
];
const pdfUrl = ref("");
const dialogVisible = ref(false);
const showIframe = (url) => {
  console.log(url);
  pdfUrl.value = url;
  dialogVisible.value = true;
};
</script>

<template>
  <div>
    <el-button v-for="url in urls" @click="showIframe(url.url)">{{
      url.name
    }}</el-button>
    <el-dialog v-model="dialogVisible">
      <iframe
        :src="'/pdfjs-dist/web/viewer.html?file=' + pdfUrl"
        frameborder="0"
      ></iframe>
      <template #footer>
        <span class="dialog-footer">
          <el-button @click="dialogVisible = false">Cancel</el-button>
        </span>
      </template>
    </el-dialog>
  </div>
</template>

<style scoped></style>
