# PowerPoint Splitter Web Application

A web application that splits PowerPoint presentations into multiple separate presentations based on slide tags in notes.

## Features

- **Upload PowerPoint files** through a user-friendly web interface
- **Automatic splitting** based on tags in slide notes
- **Universal slides** with `[*]` tag appear in all presentations
- **Downloadable results** for individual presentations or as a zip file
- **Docker containerized** for easy deployment

## How It Works

1. Add tags to your PowerPoint slides as `[tag1,tag2,tag3]` at the end of slide notes
2. Add the special tag `[*]` to slides that should appear in all presentations
3. Upload your presentation through the web interface
4. The application processes the file and creates separate presentations for each tag
5. Download individual presentations or all presentations as a zip file

## Example

If you have a presentation with 5 slides tagged as follows:
- Slide 1: `[intro,*]`
- Slide 2: `[healthcare]`
- Slide 3: `[retail]`
- Slide 4: `[healthcare,retail]`
- Slide 5: `[*]`

The application will create two presentations:
- `healthcare.pptx` containing slides 1, 2, 4, and 5
- `retail.pptx` containing slides 1, 3, 4, and 5

## Requirements

- Docker and Docker Compose

## Installation and Setup

### Using Docker Compose (Recommended)

1. Clone this repository
2. Navigate to the project directory
3. Start the application:

```bash
docker-compose up -d
```

4. Access the application at http://localhost:5001

### Using Docker Directly

```bash
docker build -t powerpoint-splitter .
docker run -p 5001:5001 -v $(pwd)/uploads:/app/uploads -v $(pwd)/output:/app/output powerpoint-splitter
```

## Usage Instructions

1. Open your web browser and go to http://localhost:5001
2. Click "Choose PowerPoint File" and select your presentation
3. Click "Upload & Process"
4. On the results page, you'll see a list of generated presentations based on slide tags
5. Click on the presentation names to download individual presentations
6. Click "Download All Files (ZIP)" to download all presentations as a zip archive
7. Click "Process Another File" to upload a different presentation
8. Click "Clear Files" to remove temporary files from the server

## Tagging Format

Add tags to your PowerPoint slides by adding text in this format to the slide notes:
```
[tag1,tag2,tag3]
```

For slides that should appear in all presentations, use the universal tag:
```
[*]
```

Tags should be placed at the end of the slide notes.

## Project Structure

```
powerpoint_splitter/
├── app.py                # Flask application
├── docker-compose.yml    # Docker Compose configuration
├── Dockerfile            # Docker configuration
├── requirements.txt      # Python dependencies
├── templates/            # HTML templates
│   ├── base.html         # Base template
│   ├── index.html        # Upload page
│   └── results.html      # Results page
├── uploads/              # Temporary storage for uploaded files
└── output/               # Storage for generated presentations
```

## Development

For local development without Docker:

1. Create a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Run the development server:
```bash
flask run
```

## License

[MIT License](https://opensource.org/licenses/MIT)

## Acknowledgements

This project is based on the PowerPoint splitter script created by Simon.