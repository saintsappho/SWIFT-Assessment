# The Assignment:

## SWIFT Frontend Assessment
The following project folder has a simple frontend page to start your project. You are tasked with the following using Vue:
<ul>
<li> This frontend is intended for a user to be able to upload a document and render a preview of that document. First convert the app.txt to app.js.
Every time a document is uploaded we want to add that document to this list of documents in the unordered list in the section with id="user-docs". <br>

If the user has not uploaded any documents, display using conditional rendering the paragraph in the paragraph tag under the user-docs section. Feel free to change this description if desired. For this task we recommend you reference the Vue documentation for conditional rendering: https://vuejs.org/guide/essentials/conditional.html this allows you to render conditional elements in the DOM. </li>

<li>Once this functionality is complete, add some styling and design to enhance the user experience, and one other feature such as converting the list of uploaded documents to a component with other information from the doc. A clear button that clears the list. Anything. Just keep in mind the law of diminishing margins! Timeliness and functionality are often most important to clients. Good luck!  </li>
</ul> 

## How it Went
This is my first time working with Vue.js, so implementing this frontend uploading and previewing functionality was an exciting challenge. 

I ran into persistent stack-overflow errors when attempting to convert the given folder into an existing Vue-SPA. I believe this is simply due to the lack of node modules and jsons. 

sooooo I started over. 

```bash
npm create vue@latest
```

Once my app was extant I deleted all the unnecessary boilerplate filler and filled in with the project seed from the assignment task.

I was able to accomplish the needed Vue functionality for dynamic updates. However, I encountered an issue when clearing the list of documents upon user action.

Despite implementing the functionality to clear the list, it seems there's a hiccup in the code preventing it from functioning as intended. I am confident that I will be able solve this issue and many others with one more day's practice in Vue. 

<ul>
<li>
I applied 1.5 hours of self-guided learning and solo-debugging but could not yet solve this problem. I'm excited to dive deeper into debugging to identify and resolve the issue after discussing the specific needs of the clients.
</li>
<li>
I worked on improving the user experience through styling and added a feature to convert the list of uploaded documents into a more informative component. 
I tried to ensure a balance between functionality and aesthetics without spending too much time in CSS beautification, as I worked to follow the law of diminishing margins.
</li>
</ul>
In summary, while I do not feel that I have fully completed the challenge, I'll be resolving this SWIFTly. In general, I'm satisfied with this as a demonstration of my capability. I look forward to further refining this SPA to meet project requirements.
