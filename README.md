# Fashion MNIST Classification API

This project implements a neural network to classify images from the Fashion MNIST dataset. The model is built using PyTorch and exposed as an API using FastAPI. The project includes training and evaluation of the model, visualizations of the training process, and an endpoint for making predictions.

## Requirements

- Python 3.7+
- FastAPI
- Uvicorn
- PyTorch
- Torchvision
- TQDM
- Seaborn
- Matplotlib
- Scikit-learn
- Pydantic

## Installation

1. Clone the repository and navigate to the project directory:
    ```bash
    git clone <repository-url>
    cd <repository-name>
    ```

2. Create a virtual environment and activate it:
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```

3. Install the required packages:
    ```bash
    pip install -r requirements.txt
    ```

## Training the Model

1. Run the Jupyter notebook to train the model:
    ```bash
    jupyter notebook Modification.ipynb
    ```
   This notebook will:
   - Download and preprocess the Fashion MNIST dataset.
   - Define and train a neural network.
   - Evaluate the model on the test dataset.
   - Save the trained model weights to `models/mnist_model.pt`.
   - Visualize the training process.

## Running the API

1. Install the required packages if not already installed:
    ```bash
    pip install fastapi uvicorn pydantic
    ```

2. Start the FastAPI server:
    ```bash
    uvicorn main:app --reload
    ```
   The API will be available at `http://127.0.0.1:8000`.

## API Endpoint

### `/model/prediction`

- **Method:** POST
- **Request Body:**
    ```json
    {
        "image": [[0.0, 0.1, ..., 0.9], [...], ..., [...]]
    }
    ```
    The `image` should be a 2D list representing the grayscale pixel values of the image.

- **Response:**
    ```json
    {
        "prediction": <predicted_class>
    }
    ```

## Example Request

You can use `curl` to make a request to the API:

```bash
curl -X POST "http://127.0.0.1:8000/model/prediction" -H "Content-Type: application/json" -d '{"image": [[0.0, 0.1, ..., 0.9], [...], ..., [...]]}'
Troubleshooting
If you encounter any issues with package installations or running the server, ensure all dependencies are installed and the virtual environment is activated.
Refer to the official documentation of FastAPI, PyTorch, and Torchvision for additional help.
