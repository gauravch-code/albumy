

`''
# Albumy

*Capture and share every wonderful moment – now with ML-powered image accessibility and search!*

Albumy is an example application for *[Python Web Development with Flask](https://helloflask.com/en/book/1)* (《[Flask Web 开发实战](https://helloflask.com/book/1)》).  
This enhanced version automatically generates alternative text for images using the Azure Computer Vision API and detects objects in images to enable keyword-based image search.

Demo: http://albumy.helloflask.com

![Screenshot](https://helloflask.com/screenshots/albumy.png)

## Installation

### 1. Clone the Repository

```bash
$ git clone https://github.com/greyli/albumy.git
$ cd albumy
```

### 2. Create and Activate a Virtual Environment

Using **venv/virtualenv** with pip:

```bash
$ python -m venv env         # For Python2, use: `virtualenv env`; on Linux/macOS, you may use `python3 -m venv env`
$ source env/bin/activate      # On Windows: `env\Scripts\activate`
$ pip install -r requirements.txt
```

Or, using **Pipenv**:

```bash
$ pipenv install --dev
$ pipenv shell
```

### 3. Configure the Azure Computer Vision API

Albumy uses the Azure Computer Vision API to generate alternative text for uploaded images and detect objects for improved image search.

1. **Sign Up for Azure Cognitive Services:**  
   - Visit [Azure Cognitive Services - Computer Vision](https://azure.microsoft.com/en-us/services/cognitive-services/computer-vision/) and create a free account (or use your existing account).
   - Create a **Computer Vision** resource to obtain your API key and endpoint.

2. **Set Up Environment Variables:**  
   In the project root, create a file named `albumyenv` (or `.env`) with the following content:

   ```ini
   AZURE_API_KEY=your_azure_api_key_here
   AZURE_ENDPOINT=https://your-resource-name.cognitiveservices.azure.com/vision/v3.2/analyze
   ```

   *Do not commit this file if it contains sensitive credentials.*

### 4. Generate Fake Data and Rebuild the Search Index

Before running the application for the first time, populate the database with fake data and rebuild the Whooshee search index so that the ML-powered search works correctly:

```bash
$ flask forge
$ flask rebuild-index
```

### 5. Run the Application

Start the development server:

```bash
$ flask run
```

Open your browser and navigate to [http://127.0.0.1:5000](http://127.0.0.1:5000) to view Albumy.

### 6. Testing the ML Features

- **Alternative Text Generation:**  
  Upload a photo via the upload page without providing your own alternative text. The system will automatically generate alternative text using the Azure API.

- **Image Search:**  
  Use the search feature to find images by keywords (for example, if a photo of a car is uploaded, searching for "car" should display that image). The detected objects are used to power the search.

### Test Account

- **Email:** `admin@helloflask.com`
- **Password:** `helloflask`

## License

This project is licensed under the MIT License (see the [LICENSE](LICENSE) file for details).
```
