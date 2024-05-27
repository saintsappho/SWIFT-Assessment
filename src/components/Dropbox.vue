<template>
  
  <section id="user-input">
    <h2>Upload PDF Document</h2>
    <!-- the drop zone!! -->
    <div id="drop-zone" @dragover.prevent @drop.prevent="handleDrop">
      <!-- ask for PDF in iframe if pdfUrl false -->
      <p v-if="!pdfUrl">Drag & drop your PDF here</p>
      <!-- display PDF in iframe if pdfUrl true -->
      <iframe v-if="pdfUrl" ref="pdfViewer" :src="pdfUrl" width="100%" height="600px"></iframe>
    </div>
    <!-- button suite for feature PDF -->
    <span v-if="pdfUrl">
      <Button text="Submit PDF" :onClick="uploadDoc" />
      <Button color="orange" text="Print" :onClick="printPdf" />
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
    // method for file drop event
    handleDrop(e) {
      const file = e.dataTransfer.files[0];
      if (file && file.type === 'application/pdf') {
        // emit change of dropped file
        this.$emit('fileDropped', file);
      } else {
        alert('Please upload a PDF file');
      }
    },
    // method to emit event on PDF submission
    uploadDoc() {
      this.$emit('submitPdf');
    },
    // method to emit event for clearing the PDF
    clearDoc() {
      this.$emit('clearPdf');
    },
    // method to print the displayed PDF
    printPdf() {
      const pdfViewer = this.$refs.pdfViewer;
      if (pdfViewer) {
        pdfViewer.contentWindow.print();
      }
    }
  }
};
</script>