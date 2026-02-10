# Image2TextApp – AppSec Focused

**Image2TextApp** is an Android application that captures images and extracts text using Google ML Kit. This version emphasizes Application Security (AppSec) principles, highlighting secure coding practices, threat mitigation, and potential vulnerabilities.

## Features

- **Secure Image Capture**: Handles device camera access with proper runtime permissions, minimizing attack surface.
- **Text Extraction**: Detects and extracts text using Google ML Kit while avoiding unsafe storage or logging of sensitive data.
- **Safe Display of Results**: Prevents exposure of sensitive information when showing extracted text.
- **Secure Data Handling**:
  - Images processed in memory; local storage encrypted if needed.
  - No sensitive data written to plaintext files or logs.
- **Input Validation & Sanitization**: Prevents injection attacks and unsafe handling of extracted text.

## Potential Vulnerabilities Highlighted

- Unencrypted storage of captured images or text.
- Insecure handling of API keys for ML Kit.
- Improper permission handling that could allow unauthorized access.
- Logging sensitive data during debugging.
- Lack of input validation could lead to injection attacks if text is later used in other contexts.

## Requirements

- Android Studio
- Android device or emulator with a camera
- Google ML Kit dependencies

## Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/nikolaivetrik24062010/Image2TextApp.git
    ```
2. Open the project in Android Studio.
3. Build and run on an Android device or emulator.

## Security Considerations

- Camera and storage permissions requested only when needed.
- All data in memory; local storage encrypted if persistence is required.
- Sensitive information never logged.
- Follows secure coding standards and safe integration with ML Kit.
- Encourages threat modeling to identify additional security gaps.

## Contributing

Contributions are welcome with a focus on security:

1. Fork the repository.
2. Create a branch for your feature or bugfix:
    ```bash
    git checkout -b feature-name
    ```
3. Commit changes with clear, security-focused messages:
    ```bash
    git commit -m "Fix vulnerability / secure implementation"
    ```
4. Push to the branch:
    ```bash
    git push origin feature-name
    ```
5. Open a pull request for review.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
