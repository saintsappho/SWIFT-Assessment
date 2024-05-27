<template>
  <div>
    <header>
      <h1>SWIFT User Documents Preview</h1>
    </header>
    
    <!-- docs upload section -->
    <section id="user-docs">
      <h2>My Documents</h2>
      <!-- input for docs -->
      <input class="input" type="file" accept="application/pdf" @change="handleFileSelect" />
      
      <!-- conditionally render if no documents are uploaded -->
      <p v-if="documents.length === 0">No documents have been uploaded yet - please upload one!</p>
      
      <!-- conditionally render when documents are uploaded: list of uploaded documents -->
      <ul>
        <li v-for="doc in documents" :key="doc.name">
          {{ doc.name }}
          <!-- button suite per doc -->
          <!-- Not yet operating correctly. -->
          <span v-if="pdfUrl">
            <!-- uploadDoc requires back end existence -->
            <Button text="Save PDF" :onClick="uploadDoc" />
            <!-- clearPdf should empty array of doc.titles. incomplete functionality -->
            <Button color="red" text="Delete PDF" :onClick="clearPdf" />
          </span>
        </li>
      </ul>
    </section>
    
    <!-- dropbox component -->
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
      // array to store uploaded docs
      documents: [],
    };
  },
  methods: {
    // click input method
    handleFileSelect(e) {
      const file = e.target.files[0];
      if (file && file.type === 'application/pdf') {
        this.addFile(file);
      } else {
        alert('Please select a PDF file');
      }
    },
    // drag dropbox method
    handleFileDrop(file) {
      if (file && file.type === 'application/pdf') {
        this.addFile(file);
      } else {
        alert('Please drag and drop a PDF file');
      }
    },
    // common submethod to add file to docs array
    addFile(file) {
      const reader = new FileReader();
      reader.onload = (e) => {
        // sets PDF URL and pushes doc to array
        this.pdfUrl = e.target.result;
        this.documents.push({ name: file.name, url: e.target.result });
      };
      reader.readAsDataURL(file);
    },
    // test method to upload a document (placeholder for future functionality)
    uploadDoc() {
      console.log('Upload button clicked: In a production build this would have a hook to submit PDF to backend.');
      // implement future upload logic here
      // implement future upload logic here
      // implement future upload logic here
    },
    // method to clear specific document from the docs array
    // currently only removes from the dropbox display and hides buttons
    clearDoc(doc) {
      const index = this.documents.indexOf(doc);
      if (index !== -1) {
        this.documents.splice(index, 1);
      }
      // not working, requires future logic
      // not working, requires future logic
      // not working, requires future logic
    },
    // method to clear the displayed PDF
    clearPdf() {
      this.pdfUrl = null;
    },
    // method for printing the displayed PDF
    printPdf() {
      this.print();
    },
  },
};
</script>

<style scoped>
/* Add future styles here */
</style>
