<template>
  <div>
    <header>
      <h1>SWIFT User Documents Preview</h1>
    </header>
    <section id="user-docs">
      <h2>My Documents</h2>
      <input class="input" type="file" accept="application/pdf" @change="handleFileSelect" />
      <!-- <Button text="Upload Doc" :onClick="uploadDoc" /> -->
      <p v-if="documents.length === 0">No documents have been uploaded yet - please upload one!</p>
      <ul>
        <li v-for="doc in documents" :key="doc.name">
          {{ doc.name }}
          <span v-if="pdfUrl">
            <Button text="Save PDF" :onClick="uploadDoc" />
            <Button color="red" text="Delete PDF" :onClick="clearPdf" />
          </span>
        </li>
      </ul>
    </section>
    <Dropbox :pdfUrl="pdfUrl" @fileDropped="handleFileDrop" @clearPdf="clearPdf" />
  </div>
</template>

<script>
import Button from './components/Button.vue';
import Dropbox from './components/Dropbox.vue';

export default {
  components: {
    Button,
    Dropbox,
  },
  data() {
    return {
      pdfUrl: null,
      documents: [],
    };
  },
  methods: {
    handleFileSelect(e) {
      const file = e.target.files[0];
      if (file && file.type === 'application/pdf') {
        this.addFile(file);
      } else {
        alert('Please select a PDF file');
      }
    },
    handleFileDrop(file) {
      if (file && file.type === 'application/pdf') {
        this.addFile(file);
      } else {
        alert('Please drag and drop a PDF file');
      }
    },
    addFile(file) {
      const reader = new FileReader();
      reader.onload = (e) => {
        this.pdfUrl = e.target.result;
        this.documents.push({ name: file.name, url: e.target.result });
      };
      reader.readAsDataURL(file);
    },
    uploadDoc() {
      console.log('Upload button clicked: In a production build this would have a hook to submit PDF to backend.');
      // Implement future upload logic here
    },
    clearDoc(doc) {
      const index = this.documents.indexOf(doc);
      if (index !== -1) {
        this.documents.splice(index, 1);
      }
    },
    clearPdf() {
      this.pdfUrl = null;
    }
  },
};
</script>

<style scoped>
/* Add your styles here */
</style>
