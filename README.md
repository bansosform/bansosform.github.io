# Bansos Registration Form

This project is a web application for registering citizens who need social assistance (Bantuan Sosial) in Indonesia, created for Lembaga Pemberdayaan Masyarakat Jawa Barat (LPM Jabar). The application is designed for easy data input by admins at the district (kecamatan) and village (kelurahan) levels and can be accessed via both smartphones and laptops.

## Features

- **Form Inputs:**
  - Full name (required)
  - NIK (National ID number, required)
  - Family card number (required)
  - Photo upload for KTP and Family card (Max size: 2MB, supported formats: JPG/JPEG/PNG/BMP)
  - Age (must be 25 years old or older)
  - Gender (Male/Female)
  - Address details (Province, Kab/Kota, Kecamatan, Kelurahan/Desa, RT/RW)
  - Income before and after the pandemic
  - Reasons for requiring assistance
  - Checkbox for data declaration
- **Form Validation:**

  - All fields are required.
  - Age validation (must be ≥ 25 years old).
  - Image file size and format validation for KTP and family card uploads.

- **Data Preview:**

  - Once the form is submitted, the entered data will be displayed on a preview page.

- **Submission Simulation:**
  - Simulated backend service response time (1500ms) using `Math.random()` to simulate both success and failure cases.

## Tech Stack

- **Frontend:**

  - Vue.js
  - Axios (for API calls)

- **API Services:**

  - Emsifa API for fetching Indonesia’s provinces, cities, districts, and villages. Documentation: [Emsifa API](https://www.emsifa.com/api-wilayah-indonesia/)

- **Hosting:**
  - Deployed using [Github Pages](https://www.netlify.com/) (or other free-tier hosting services like Github Pages, Surge, Firebase Hosting, etc.)

## Simulation Details

- Backend service responses are simulated with a delay of 1500ms.
- Error simulation using `Math.random()` to occasionally produce "Internal Server Error."
