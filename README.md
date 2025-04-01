<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Silent Scholars - Study Notes Upload</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }

        header {
            background-color: #4CAF50;
            color: white;
            padding: 1em 0;
            text-align: center;
        }

        main {
            padding: 20px;
            max-width: 800px;
            margin: auto;
            background-color: white;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }

        form {
            margin-bottom: 20px;
        }

        input[type="text"], input[type="file"] {
            padding: 10px;
            margin: 5px 0;
            width: calc(100% - 22px);
            border: 1px solid #ccc;
            border-radius: 4px;
        }

        button {
            padding: 10px 15px;
            background-color: #4CAF50;
            color: white;
            border: none;
            cursor: pointer;
            border-radius: 4px;
        }

        button:hover {
            background-color: #45a049;
        }

        ul {
            list-style-type: none;
            padding: 0;
        }

        li {
            margin-bottom: 10px;
        }

        footer {
            text-align: center;
            padding: 20px;
            background-color: #4CAF50;
            color: white;
            position: relative;
            bottom: 0;
            width: 100%;
        }
    </style>
</head>
<body>
    <header>
        <h1>Silent Scholars</h1>
        <h2>Electrical Engineering Study Notes Upload</h2>
    </header>
    <main>
        <h3>Upload Your Notes</h3>
        <form id="uploadForm">
            <input type="text" id="noteTitle" placeholder="Enter Note Title" required />
            <input type="file" id="noteFile" required />
            <button type="submit">Upload Note</button>
        </form>
        <h4>Uploaded Notes</h4>
        <ul id="notesList">
            <!-- Uploaded notes will be displayed here -->
        </ul>
    </main>
    <footer>
        <p>&copy; 2023 Silent Scholars - Electrical Engineering Notes</p>
    </footer>
    <script>
        const uploadForm = document.getElementById('uploadForm');
        const notesList = document.getElementById('notesList');

        // Handle form submission
        uploadForm.addEventListener('submit', function(event) {
            event.preventDefault(); // Prevent form from submitting normally

            const noteTitle = document.getElementById('noteTitle').value;
            const noteFile = document.getElementById('noteFile').files[0];

            if (noteTitle && noteFile) {
                // Create a list item
                const listItem = document.createElement('li');
                listItem.textContent = `${noteTitle} (${noteFile.name})`;

                // Create a link for download
                const link = document.createElement('a');
                link.href = URL.createObjectURL(noteFile);
                link.download = noteFile.name;
                link.textContent = ' (Download)';
                listItem.appendChild(link);

                // Add the list item to the notes list
                notesList.appendChild(listItem);

                // Clear the form
                uploadForm.reset();
            }
        });
    </script>
</body>
</html>
