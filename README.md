# Modular Resume Repository

This repository contains my personal resumes, designed with a modular, component-based LaTeX architecture. It allows me to easily manage and tailor resumes for different roles (e.g., Python Developer, Machine Learning Engineer) without duplicating code or content.

## Repository Structure

The repository is divided into small, reusable LaTeX components:

- **`base/`**: Contains core configurations (`setup.tex`), contact information, education, and awards.
- **`experience/`**: Each job or internship has its own `.tex` file (e.g., `gulzarsoft.tex`, `isl.tex`).
- **`projects/`**: Each personal or academic project has its own `.tex` file.
- **`skills/`**: Role-specific skill sets (e.g., `python_dev.tex`, `ml_engineer.tex`).
- **`case_studies/`**: Detailed Markdown write-ups for specific projects, tracking the problem, approach, and technical challenges faced.
- **Role-specific Resumes**: 
  - `Template/CV.tex` (Base / General Resume)
  - `Python/Python-developer.tex`
  - `Machine Learning/machine_learning.tex`

## How it Works

Instead of writing a full resume in one file, the role-specific resumes simply `\input{}` the necessary modules. This makes updating a project or adding a new role completely seamless.

### Adding a New Project
1. Create a new file in `projects/` (e.g., `projects/my_new_app.tex`).
2. Add the project details using the custom resume commands.
3. Open the resume file you want to update (e.g., `Python/Python-developer.tex`).
4. Add `\input{../projects/my_new_app.tex}` in the Projects section.

## Build using Docker

You can compile the resumes into PDFs using Docker without needing a local LaTeX installation.

```sh
docker build -t latex .

# Compile the Python Developer resume:
docker run --rm -i -v "${PWD}:/data" latex pdflatex Python/Python-developer.tex

# Compile the Machine Learning resume:
docker run --rm -i -v "${PWD}:/data" latex pdflatex "Machine Learning/machine_learning.tex"

# Compile the Base CV:
docker run --rm -i -v "${PWD}:/data" latex pdflatex Template/CV.tex
```

## Preview

![Resume Screenshot](/resume_preview.png)

## License

Format is MIT but all the personal data, project details, and case studies are owned by Arslan Khalid.
