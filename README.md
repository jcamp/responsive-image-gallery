# responsive-image-gallery
A modern responsive image gallery, written for html web sites in pure CSS and JS

## Responsive image gallery on a web page

### HTML

HTML: First, we need to create the HTML structure for the gallery. We can create a container element with the class "gallery", and inside it, we can create a set of image elements. Each image element should have a "data-src" attribute with the URL of the full-size image.

```
<div class="gallery">
  <img data-src="image1-full.jpg" src="image1-thumb.jpg">
  <img data-src="image2-full.jpg" src="image2-thumb.jpg">
  <img data-src="image3-full.jpg" src="image3-thumb.jpg">
  ...
</div>
```

### CSS

CSS: Next, we need to add CSS styles to make the gallery responsive. We can use CSS Grid to create a grid layout that adjusts to the screen size. We can also set the width and height of the image elements to fit the grid cells and add some padding to create some space between the images.

```
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 10px;
}

.gallery img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  padding: 5px;
}
```

### JAVASCRIPT

JavaScript: Finally, we need to add JavaScript code to handle the lightbox effect. We can create an event listener for the click event on the image elements and show the full-size image in a modal dialog when the image is clicked. We can also add an event listener for the click event on the modal dialog to close the dialog when the user clicks outside the image or on a close button.

```
// get the gallery container element
const gallery = document.querySelector('.gallery');

// add a click event listener to all the image elements
gallery.addEventListener('click', event => {
  if (event.target.tagName === 'IMG') {
    // create a modal dialog element
    const modal = document.createElement('div');
    modal.classList.add('modal');

    // create an image element to show the full-size image
    const image = document.createElement('img');
    image.src = event.target.dataset.src;

    // create a close button element
    const close = document.createElement('button');
    close.textContent = 'Close';

    // add the image and close button elements to the modal dialog
    modal.appendChild(image);
    modal.appendChild(close);

    // add a click event listener to the modal dialog
    modal.addEventListener('click', event => {
      if (event.target === modal || event.target === close) {
        // remove the modal dialog when the user clicks outside the image or on the close button
        modal.remove();
      }
    });

    // add the modal dialog to the document
    document.body.appendChild(modal);
  }
});
```
