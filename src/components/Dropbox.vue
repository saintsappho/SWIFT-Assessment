<template>
  <section id="user-input">
    <h2>Upload PDF Document</h2>
    <div id="drop-zone" @dragover.prevent @drop.prevent="handleDrop">
      <p v-if="!pdfUrl">Drag & drop your PDF here</p>
      <iframe v-if="pdfUrl" :src="pdfUrl" width="100%" height="600px"></iframe>
    </div>
    <span v-if="pdfUrl">
      <Button text="Submit PDF" :onClick="uploadDoc" />
      <Button color="red" text="Clear PDF" :onClick="clearDoc" />
    </span>
  </section>
</template>

<script>
import Button from './Button.vue';

export default {
  name: 'Dropbox',
  components: {
    Button
  },
  props: {
    pdfUrl: String,
  },
  methods: {
    handleDrop(e) {
      const file = e.dataTransfer.files[0];
      if (file && file.type === 'application/pdf') {
        this.$emit('fileDropped', file);
      } else {
        alert('Please upload a PDF file');
      }
    },
    uploadDoc() {
      this.$emit('submitPdf');
    },
    clearDoc() {
      this.$emit('clearPdf');
    }
  }
};
</script>
