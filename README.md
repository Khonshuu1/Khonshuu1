<!DOCTYPE html>
<html>
<head>
  <title>Subir y Publicar Fotos</title>
  <link rel="stylesheet" type="text/css" href="styles.css">
</head>
<body>
  <h1>Subir y Publicar Fotos</h1>

  <div id="upload-form">
    <input type="file" id="file-input">
    <button id="upload-button">Subir Foto</button>
  </div>

  <div id="gallery"></div>

  <script src="script.js"></script>
</body>
</html>

body {
  font-family: Arial, sans-serif;
  text-align: center;
  background-color: #f2f2f2;
}

h1 {
  margin-top: 20px;
}

#upload-form {
  margin-top: 20px;
}

#file-input {
  display: none;
}

#upload-button {
  padding: 10px 20px;
  background-color: #4CAF50;
  color: white;
  border: none;
  cursor: pointer;
}

#gallery {
  margin-top: 20px;
}

.photo {
  display: inline-block;
  margin: 10px;
}

.photo img {
  width: 300px;
  height: 300px;
  object-fit: cover;
}

document.getElementById('upload-button').addEventListener('click', function() {
  document.getElementById('file-input').click();
});

document.getElementById('file-input').addEventListener('change', function(event) {
  var file = event.target.files[0];
  var reader = new FileReader();

  reader.onload = function(e) {
    var imageSrc = e.target.result;
    var gallery = document.getElementById('gallery');

    var photoContainer = document.createElement('div');
    photoContainer.classList.add('photo');

    var photo = document.createElement('img');
    photo.src = imageSrc;

    photoContainer.appendChild(photo);
    gallery.appendChild(photoContainer);
  }

  reader.readAsDataURL(file);
});
