# Take-Home Assignment: Art Gallery Explorer

Thank you for your interest in the role. This assignment is designed to give you an opportunity to showcase your skills in building a modern Android application by following a clear technical specification.

**Timeline:** Mostly you have **one week** to complete and submit this assignment.

---

### API Specification

You will use the official Art Institute of Chicago (AIC) API. It is free and requires no authentication.

*   **API Documentation:** [https://api.artic.edu/docs/](https://api.artic.edu/docs/)
*   **Base URL:** `https://api.artic.edu/api/v1`

#### Data Endpoints

1.  **List Artworks (Initial Load):**
    *   **URL:** `https://api.artic.edu/api/v1/artworks?fields=id,title,image_id,artist_display`

2.  **Search Artworks:**
    *   **URL Structure:** `https://api.artic.edu/api/v1/artworks/search?q={your_query}&fields=id,title,image_id,artist_display`

3.  **Artwork Details:**
    *   **URL Structure:** `https://api.artic.edu/api/v1/artworks/{artwork_id}?fields=image_id,title,artist_display,place_of_origin,date_display,description`

#### Image Construction (IIIF)

*   **Base Image URL:** `https://www.artic.edu/iiif/2`
1.  **List/Search Thumbnail Image (200px wide):**
    *   **URL Structure:** `{Base Image URL}/{image_id}/full/200,/0/default.jpg`
2.  **Detail Screen Image (843px wide):**
    *   **URL Structure:** `{Base Image URL}/{image_id}/full/843,/0/default.jpg`

---

### Design Specification

The UI for this assignment should be implemented based on the designs provided in the following Figma file. The file includes designs for the Gallery Screen, Detail Screen, and Empty/Error states.

*   **Figma Link:** [https://www.figma.com/design/1rclEytCv4zDzICNcXrcc0/UI-for-hiring-team?node-id=14044-13986&p=f&t=j55ehp4XU887IWMo-0](https://www.figma.com/design/1rclEytCv4zDzICNcXrcc0/UI-for-hiring-team?node-id=14044-13986&p=f&t=j55ehp4XU887IWMo-0)

**Note:** This Figma file is password-protected. If you have not received the password in your email, please ask your HR contact for access.

---

### Core Requirements

1.  **Artwork Gallery Screen:**
    *   On app launch, fetch and display the initial list of artworks.
    *   Include a search bar. When a user submits a query, display the search results.
    *   Each item in the gallery must display the artwork's thumbnail (200px), title, and artist's name.
    *   Implement and display appropriate UI for loading and error states.

2.  **Artwork Detail Screen:**
    *   On tapping an artwork, navigate to a detail screen.
    *   Fetch and display the artwork's full details, including the high-quality image (843px), title, artist, date, dimensions, credit line, and description.
    *   *Note: The description field may contain HTML tags. Please parse and display this as plain text.*

3.  **Architecture & Kotlin Fundamentals:**
    *   **UI:** The entire application UI must be built with **Jetpack Compose**.
    *   **Architecture:** Implement a clean MVVM or MVI architecture.
    *   **Kotlin:** Your code should be idiomatic and demonstrate a strong grasp of Kotlin fundamentals.
    *   **Concurrency:** All network calls must be handled with **Kotlin Coroutines**.

### Bonus Points (Showcasing Advanced Skills)

Completing the following is not required, but will be viewed very favorably as it demonstrates a deeper level of expertise.

*   **Robust Pagination / Infinite Scrolling:**
    *   Implement infinite scrolling on the main gallery screen.
    *   Your implementation **must** correctly parse the `pagination` object from the API response and use the `next_url` provided within it to load subsequent pages.

*   **Robust State & UI:**
    *   **Handle Configuration Changes:** The app must correctly handle screen rotation. The current state (search query, results, scroll position, and `next_url`) should be preserved without re-fetching data.
    *   **Image Loading:** Use a modern image loading library like **Coil**, including placeholder and error images.

*   **Clean Data Layer & Domain Model:**
    *   Implement a **Repository Pattern** to abstract data sources.
    *   Map the complex API response objects to simpler, clean domain models for use throughout the app.

*   **Testing:**
    *   Write **JUnit unit tests** for your ViewModels, mocking dependencies to verify that your `StateFlow` emits the correct UI states under various conditions.

---

### Submission Instructions

Please follow these steps carefully.

1.  **Create a `README.md` file:**
    *   If your project has any special requirements (e.g., a specific JDK version, Android SDK version, or special build steps), you **must** document them in this file.
    *   If this file is empty or does not specify requirements, we will attempt to run it on our default tester machine setup.

2.  **Clean Your Project:**
    *   This step prepares your project for submission by removing temporary build files.

    > **WARNING:** The following command is destructive and will irreversibly remove all untracked files and directories from your project folder. This includes any new code files you have created but not yet committed.
    >
    > **It is critical that you commit all of your necessary work *before* running this command.** Double-check your `git status` to ensure there are no uncommitted changes you wish to keep.
    >
    > ---
    >
    > **PERINGATAN (Bahasa Indonesia):** Perintah berikut ini bersifat **destruktif** dan akan **menghapus secara permanen** semua file dan direktori yang tidak terlacak (*untracked*) dari folder proyek Anda. Ini termasuk file kode baru yang telah Anda buat tetapi **belum di-commit**.
    >
    > **Sangat penting bagi Anda untuk melakukan `commit` pada semua pekerjaan Anda *sebelum* menjalankan perintah ini.** Periksa kembali `git status` Anda untuk memastikan tidak ada perubahan yang belum di-commit yang ingin Anda simpan.

    *   Once you have committed everything, run the following command from your project's root directory:
        ```bash
        git clean -dfx
        ```

3.  **Create the Patch File(s):**
    *   We expect the submission in the `git format-patch` format. This command creates a file for each commit you have made.
    *   Assuming your work is on a branch and you want to create patches against the `main` branch, run:
        ```bash
        git format-patch main
        ```
    *   This will generate one or more `.patch` files in your project's root directory (e.g., `0001-feat-add-gallery-screen.patch`).

4.  **Submit:**
    *   Email the generated `.patch` file(s) to us.

**Important:** Your submission **must** be able to be applied and built successfully. A project that fails to build may be disqualified. We recommend you do a final test by cloning your repository to a new folder, applying your own patch, and confirming it builds before submitting.
