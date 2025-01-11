# Multimodal-Document-Analysis-and-Query-Retrieval

This script automates the following tasks:

Download PDF documents from the web
A collection of PDF documents is downloaded and saved locally for further processing.

Convert PDF pages to images
Each page of the PDF is converted into an image using the pdf2image library.

Visualize the converted images
The script dynamically generates a grid to display the images for inspection or presentation purposes.

Index images for retrieval
Using the byaldi library, images are indexed for semantic search based on their content.

Retrieve relevant images using a natural language query
A query is executed against the indexed images to retrieve pages (images) that are contextually relevant.

Analyze retrieved images using visual-language models (VL models)
Multiple VL models (RAGMultiModalModel, Qwen2VL, and Blip2) are employed to answer queries or extract insights from the retrieved images.

Steps Explained
1. Download PDFs
A dictionary (pdfs) maps names to their respective URLs.
PDFs are downloaded and saved in the dataset directory using Python's requests library.
2. Convert PDFs to Images
The convert_from_path function from the pdf2image library is used to convert each PDF page into images.
The images are stored in a dictionary (all_images) where the keys are document IDs and the values are lists of images (one per page).
3. Visualize Converted Images
Images from a specific PDF are displayed using Matplotlib in a grid format. The grid size is dynamically calculated based on the number of images.
4. Index Images for Semantic Search
The RAGMultiModalModel from the byaldi library indexes the images for semantic search.
The indexed images are stored in a searchable index (image_index).
5. Query and Retrieve Relevant Images
A natural language query (e.g., "What role does passive design play in creating sustainable houses?") is executed against the indexed images.
The RAGMultiModalModel.search method retrieves the most relevant images based on the query.
The get_result_images function extracts the corresponding images from the all_images dictionary.
6. Analyze Retrieved Images with Visual-Language Models


Two visual-language models (Qwen2VL and Blip2) are used to analyze the retrieved images:

Qwen2VL:
The images and query are formatted into a chat template.
The model generates text responses that summarize or answer the query based on the images.


Blip2:
The images and query are similarly formatted into a chat template.
The model generates text responses based on the visual content of the images.
Dependencies

The script relies on the following libraries:

1. requests: For downloading the PDFs.
2. pdf2image: For converting PDF pages to images.
3. matplotlib: For visualizing images.
4. byaldi: For indexing images and performing semantic search.
5. transformers: For loading and using visual-language models.
6. torch: For handling computations on GPU for VL models.
7. System packages: poppler-utils: Required by pdf2image for PDF conversion.



How to Run:

Step 1: Install Dependencies
Install the necessary Python libraries and system packages:

!pip install byaldi pdf2image qwen-vl-utils transformers

!apt-get install -y poppler-utils

Step 2: Download and Process PDFs
Run the script to download the PDFs, convert them into images, and index them for retrieval.

Step 3: Perform a Query
Modify the query variable with a natural language query and execute the script to retrieve relevant images.

Step 4: Analyze Results
The script automatically uses two VL models (Qwen2VL and Blip2) to generate responses based on the retrieved images.

Example Output:

Downloaded PDFs
PDFs downloaded successfully!
Converted Images
Converted Windows.pdf to 10 images.
Converted Roofs.pdf to 15 images.
...


Retrieved Results:

Relevant images (pages) for the query are displayed.


Generated Text Responses:

Output from Qwen2VL:
"Passive design plays a critical role in reducing energy consumption..."

Output from Blip2:
"Passive strategies ensure natural ventilation and effective thermal insulation."

