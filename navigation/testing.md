---
layout: page
title: Testing
permalink: /testing/
---

<button id="addButton">Add Image</button>
    <button id="removeButton">Remove Image</button>
    <div id="imageContainer"></div>

<script>
    document.getElementById('addButton').addEventListener('click', function() {
        const img = document.createElement('img');
        img.src = 'https://cars.usnews.com/static/images/Auto/izmo/i159615770/2024_honda_civic_hatchback_sideview.jpg'; // Replace with your image URL
        img.alt = 'Image';
        document.getElementById('imageContainer').appendChild(img);
    });

    document.getElementById('removeButton').addEventListener('click', function() {
        const container = document.getElementById('imageContainer');
        const lastImage = container.lastElementChild;
        if (lastImage) {
            container.removeChild(lastImage);
        } else {
            alert("No images to remove!");
        }
    });
</script>