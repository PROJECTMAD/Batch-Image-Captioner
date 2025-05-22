# Batch Image Captioner (short: BiCaption)

---

## ✨ Live Demo Available! ✨

Experience BiCaption in action using: **[GitHub Pages](https://projectmad.github.io/Batch-Image-Captioner/)**

---

**Unlock the power of AI-driven image understanding with unparalleled efficiency. BiCaption is a sophisticated, client-side web application designed for batch-processing images to generate high-quality, contextually relevant captions using your own compatible local or remote OpenAI-compatible API endpoints.**

Engineered for discerning users who demand control, flexibility, and precision, BiCaption offers a streamlined workflow for transforming visual data into descriptive text, suitable for a multitude of applications including dataset preparation, content indexing, accessibility enhancements, and creative inspiration.

---

## Key Architectural & Feature Highlights:

**1. Flexible Image Input & Management:**
   - **Multi-Source Ingestion:** Seamlessly load images via:

     - **Direct Upload:** Standard file browser with multi-select capabilities.
     - **URL Pasting:** Ingest images directly from web URLs (CORS permitting).
     - **Clipboard Pasting:** Intuitive drag-and-drop or Ctrl/Cmd+V pasting of image data directly into the application or dedicated paste zone.

   - **Persistent Queue:** A dedicated, interactive queue panel displays all loaded images, their processing status, generated outputs, and management controls.
   - **Unique Image Naming:** Automatic generation of memorable, pronounceable (AdjectiveNoun) names for easy identification of images within the queue.

**2. Advanced Prompt Engineering & Model Interaction:**
   - **Dual Prompt Strategies:** Choose between two specialized prompt types tailored for different captioning needs:

     - **Stable Diffusion Prompt:** Generates detailed, descriptive prompts suitable as input for text-to-image models like Stable Diffusion, capturing artistic style, composition, and subject matter.
     - **Danbooru Tags:** Produces a comma-separated list of Danbooru-style tags (lowercase_with_underscores), meticulously ordered (artist, copyright, character, meta, general) for precise content categorization and search.

   - **Custom OpenAI-Compatible API Integration:**

     - **Full Endpoint Control:** Configure the Base URL, Chat Completion Path, and select your preferred LLM model from a dynamically fetched list.
     - **API Key Management:** Securely store and utilize your API key (optional, depending on your endpoint's authentication).
     - **Connection Testing:** Integrated API testing functionality to verify model availability and chat endpoint reachability before committing to processing.
     - **Robust Error Handling:** Clear feedback on API connection issues, model loading failures, and processing errors.

**3. Intelligent Processing & Output Customization:**
   - **Batch Processing Engine:** Efficiently process the entire queue of pending images with a single click.
   - **Individual Item Regeneration:**

     - **Immediate Feedback:** Regenerate captions for individual images on-demand without re-adding them to the queue.
     - **Dynamic Prompt Switching:** Effortlessly switch the global prompt type (Stable Diffusion / Danbooru) and regenerate an existing item's caption using the new strategy.

   - **Sophisticated Output Filtering:** Intelligent, prompt-type-specific post-processing of API responses to remove boilerplate, unwanted artifacts (e.g., "Here's your prompt:"), and forbidden terms (e.g., artist names, watermarks from SD prompts unless explicitly part of the image).
   - **Configurable Export Formats:**

     - **RAW Text Export:** Concatenate all generated captions with a user-defined delimiter (e.g., `\n\n`, `, `).
     - **Customizable JSON Export:** Define a flexible JSON schema template with placeholders (`{{timestamp}}`, `{{prompt_type}}`, `{{outputs_map_indexed}}`, `{{outputs_map_titled}}`, `{{outputs_array_detailed}}`) to structure the output precisely to your needs. Includes current app version and export timestamp by default.

   - **Per-Item & Batch Export Controls:**
     - Copy individual captions to the clipboard.
     - Copy or download all successfully generated captions in your chosen format (RAW/JSON).
     - Filenames for downloads automatically include the prompt type used and a timestamp for easy organization.

**4. Refined User Experience & Interface:**
   - **Material Design Aesthetics:** Clean, modern, and responsive interface built with Materialize CSS.
   - **Light/Dark Theme:** Switch between themes for optimal viewing comfort, with settings persisted in local storage.
   - **Interactive Console Log:** Real-time feedback on application events, image loading, processing progress, API interactions, and errors, complete with timestamps and durations.
   - **Tooltips & Helper Text:** Informative tooltips and contextual help throughout the application.
   - **Persistent Settings:** All API configurations, theme preferences, and output format settings are saved locally in the browser for convenience.
   - **Keyboard Shortcuts:** Global paste (Ctrl/Cmd+V) for images and URLs directly into relevant input modes.
   - **Responsive Design:** Adapts to various screen sizes, though primarily optimized for desktop use due to the nature of batch processing.

**5. Client-Side Architecture & Data Privacy:**
   - **Purely Client-Side Operation (excluding API calls):** All image processing, queue management, and UI logic run directly in your browser. Images are converted to base64 and sent to *your configured API endpoint*. **No image data is sent to or stored on any third-party servers by BiCaption itself.**
   - **Local Storage Utilization:** Leverages browser local storage for user settings and preferences, ensuring data persistence across sessions without server-side accounts.

---

## Technical Stack:

-   **Frontend:** HTML5, CSS3 (Materialize CSS framework), Vanilla JavaScript (ES6+)
-   **API Interaction:** `fetch` API for asynchronous communication with OpenAI-compatible endpoints.
-   **Data Handling:** Base64 encoding for image data, JSON for API payloads and structured exports.

---

## Use Cases:

-   **AI Researchers & Developers:** Rapidly generate caption datasets for model training and fine-tuning.
-   **Content Creators & Managers:** Quickly create descriptive metadata for large image libraries, improving SEO and searchability.
-   **Digital Artists & Designers:** Brainstorm and iterate on concepts by generating diverse textual interpretations of visual ideas.
-   **Accessibility Advocates:** Generate alt-text for images to make web content more accessible.
-   **Hobbyists & Enthusiasts:** Explore the capabilities of multimodal AI and experiment with different captioning styles.

---

## Getting Started:

1.  **Clone or Download:** Obtain the `index.html` file.
2.  **Open in Browser:** Simply open `index.html` in a modern web browser (Chrome, Firefox, Edge recommended).
3.  **Configure API Settings:**
      - Click the "Settings" (gear) icon.
      - Enter your OpenAI-compatible API **Base Server URL** (e.g., `http://localhost:1234` if local, or your cloud provider's endpoint).
      - Verify/adjust the **Chat Completion Path** (default: `/v1/chat/completions`).
      - Click "Test API Only". Models should load. If your API requires it, enter your **API Key**.
      - Select your desired **Model**.
      - Test the connection again if necessary.
      - Click "Save All Settings".
4.  **Load Images:** Use the "Upload," "From URL," or "Paste" tabs.
5.  **Choose Prompt Type:** Select either "Stable Diffusion Prompt" or "Danbooru Tags."
6.  **Process:**
      - Click "Process Queue" for batch operation.
      - Or, after an item is processed, click its "Regenerate" (sync) icon for individual reprocessing (potentially with a different prompt type selected globally).
7.  **Export:** Use the "Copy All" or "Download All" buttons in the queue panel, or copy individual outputs.

---

## Important Considerations & Usage Notes:

**1. Display Requirements:**
   - For an optimal user experience and to ensure all interface elements are displayed correctly, a minimum screen resolution of **1280x800 pixels (width x height)** is recommended. The application is primarily designed for desktop use.

**2. Model Compatibility & Specialization:**
   - BiCaption is designed to interface with OpenAI-compatible API endpoints. For best results and meaningful captions, the selected Language Model (LLM) on your backend server **must be a multimodal model specifically trained for vision and image captioning tasks.** General-purpose text-only LLMs will not be able to process image data or generate relevant visual descriptions. Examples of suitable architectures include those based on Llava, MiniGPT-4, or similar vision-language models.

**3. Target Audience & Default Prompting:**
   - While BiCaption is a versatile tool, its default prompt strategies (especially "Danbooru Tags") and the example image naming conventions (using AdjectiveNoun lists that include whimsical terms) are particularly well-suited for users dealing with **anime-styled imagery and character art.** The Danbooru tagging system is prevalent within such communities, making this tool highly effective for cataloging and describing this specific genre of visual content. However, the "Stable Diffusion Prompt" option and the underlying API flexibility allow for broader applications.

---

**License:** This software is released under the **MIT License**.


    MIT License

    Copyright (c) 2025 PROJECTMAD

    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in all
    copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    SOFTWARE.


---

**Modifications & Contributions:** You are fully permitted and encouraged to modify, extend, and adapt the codebase to suit your specific requirements. Contributions, bug reports, and feature suggestions are welcome. Please feel free to fork the repository and submit pull requests.
