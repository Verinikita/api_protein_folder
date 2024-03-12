API-PROTEIN-FOLDER
Este proyecto es una API REST Flask que proporciona funcionalidades para la gestión de archivos relacionados con proteínas.

Ejecución del Proyecto en Local
Para ejecutar este proyecto en tu máquina local, sigue estos pasos:

Clonar el Repositorio:
git clone https://github.com/ramaffei/api-protein-folder.git
Crear un Entorno Virtual (opcional pero recomendado):
python -m venv venv
Activar el Entorno Virtual:
En Windows:
venv\Scripts\activate
En macOS y Linux:
source venv/bin/activate
Instalar los Requerimientos:
pip install -r requirements.txt
Ejecutar la Aplicación Flask en Modo Debug:
flask --app app run --debug
Endpoints
1. /upload
Descripción: Este endpoint recibe un archivo zip y retorna un JSON con las rutas relativas de los archivos descomprimidos, organizados por extensiones.
Ejemplo de Uso en JavaScript con Fetch:
fetch('http://localhost:5000/upload', {
  method: 'POST',
  body: formData // FormData object with 'zipFile' key containing the zip file
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
2. /pdb/
Descripción: Este endpoint recibe un JSON con un parámetro obligatorio "filenames", que es un array con las rutas relativas de ciertos archivos, y un parámetro opcional "ignored_residues" que es booleano.
Ejemplo de Uso en JavaScript con Fetch:
const requestData = {
  filenames: ['file1.pdb', 'file2.pdb'],
  ignored_residues: true
};

fetch('http://localhost:5000/pdb/', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify(requestData)
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
3. /pdb/plots
Descripción: Este endpoint recibe un JSON con un parámetro obligatorio "filenames" y retorna una imagen en base64.
Ejemplo de Uso en JavaScript con Fetch:
const requestData = {
  filenames: ['file1.pdb', 'file2.pdb']
};

fetch('http://localhost:5000/pdb/plots', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify(requestData)
})
.then(response => response.blob())
.then(blob => {
  const imageURL = URL.createObjectURL(blob);
  // Use imageURL to display the image
})
.catch(error => console.error('Error:', error));
¡Listo! Ahora puedes utilizar esta API en tu entorno local para gestionar archivos relacionados con proteínas. Si tienes alguna pregunta, no dudes en contactarme.# api-protein-folder
