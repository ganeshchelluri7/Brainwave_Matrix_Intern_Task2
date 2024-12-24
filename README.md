# Noble Treasures - Cloud Deployment

## Overview
This repository provides the complete setup and deployment instructions for the **Noble Treasures** website. The project demonstrates how to upload images and static files to **Google Cloud Storage**, configure necessary permissions for public access, and update the website code to refer to these cloud-hosted assets. The website is focused on showcasing high-end products, including fragrances, bags, and watches.

## Table of Contents
1. [Google Cloud Setup](#google-cloud-setup)
   - [1.1 Create a Google Cloud Project](#11-create-a-google-cloud-project)
   - [1.2 Enable Google Cloud Storage API](#12-enable-google-cloud-storage-api)
   - [1.3 Create a Cloud Storage Bucket](#13-create-a-cloud-storage-bucket)
   - [1.4 Upload Website Files](#14-upload-website-files)
2. [Set Permissions for Public Access](#set-permissions-for-public-access)
   - [2.1 Set Read Access on Images](#21-set-read-access-on-images)
   - [2.2 Set Bucket Public Read Access](#22-set-bucket-public-read-access)
3. [Modify HTML to Use Cloud-Hosted Images](#modify-html-to-use-cloud-hosted-images)
4. [Test the Website](#test-the-website)
5. [Troubleshooting](#troubleshooting)
6. [Conclusion](#conclusion)
7. [License](#license)

---

## 1. Google Cloud Setup

### 1.1 Create a Google Cloud Project
1. Go to the [Google Cloud Console](https://console.cloud.google.com/).
2. Click on **"Select a project"** on the top bar.
3. Click on **"New Project"** and provide the project details:
    - Project Name: `Noble Treasures`
    - Location: `No organization` (or your desired location)
4. Click on **Create** to initialize the project.

### 1.2 Enable Google Cloud Storage API
1. In the Google Cloud Console, navigate to **API & Services > Dashboard**.
2. In the top search bar, search for **Google Cloud Storage** and select the **Cloud Storage API**.
3. Click **Enable** to activate Cloud Storage.

### 1.3 Create a Cloud Storage Bucket
Once your project is created and the Cloud Storage API is enabled:
1. Open **Google Cloud Console**, go to **Storage**.
2. Click **Create Bucket**.
3. Set the following parameters for your bucket:
    - **Name**: `nobletreasures` (or any custom name)
    - **Location type**: `Multi-region`
    - **Location**: Choose the location (e.g., `asia`)
    - **Storage class**: `Standard`
4. Click **Create** to create the bucket.

### 1.4 Upload Website Files
Your website includes:
- HTML and CSS files.
- Images for product showcases stored in an `/images/` directory.

To upload files into the bucket:
1. Install **Google Cloud SDK** or use the Cloud Console with **Google Cloud Shell**.
2. Use **gsutil** to upload the website files:
   - **For index.html**: 
     ```bash
     gsutil cp index.html gs://nobletreasures/
     ```
   - **For styles (e.g., style.css)**:
     ```bash
     gsutil cp style.css gs://nobletreasures/
     ```
   - **For images in the `images/` folder**:
     ```bash
     gsutil cp -r images/* gs://nobletreasures/images/
     ```

---

## 2. Set Permissions for Public Access

### 2.1 Set Read Access on Images
To ensure that users can access images, configure the permissions for each image. 
Run the following command for each image:

```bash
gsutil acl ch -u AllUsers:R gs://nobletreasures/images/DIOR\ OUD\ ISPAHAN.jpeg
gsutil acl ch -u AllUsers:R gs://nobletreasures/images/DIOR\ POISON.jpeg
gsutil acl ch -u AllUsers:R gs://nobletreasures/images/DIOR\ Saddle\ Shoulder\ Bag\ Black.jpg
Alternatively, you can recursively give read access to all images in the /images/ directory:

bash
Copy code
gsutil -m acl ch -r -u AllUsers:R gs://nobletreasures/images/
2.2 Set Bucket Public Read Access
Allow public access to all files in your bucket using the following IAM command:

bash
Copy code
gsutil iam ch allUsers:objectViewer gs://nobletreasures
This makes all objects in the bucket publicly viewable, including images and other files you upload.

3. Modify HTML to Use Cloud-Hosted Images
Once the images are uploaded and permissions are set, update your index.html and other HTML files to reference the cloud-hosted URLs for images.

To use cloud-hosted URLs for images, follow this structure:

plaintext
Copy code
https://storage.googleapis.com/<bucket_name>/<path_to_image>
For example, your index.html should include images like this:

html
Copy code
<img src="https://storage.googleapis.com/nobletreasures/images/DIOR%20OUD%20ISPAHAN.jpeg" alt="DIOR OUD ISPAHAN">
<img src="https://storage.googleapis.com/nobletreasures/images/DIOR%20POISON.jpeg" alt="DIOR POISON">
Make sure to replace spaces in filenames with %20 (URL encoding) as demonstrated above.

4. Test the Website
To test the website:

Visit the index.html file hosted on the Google Cloud Storage bucket via the following URL:

plaintext
Copy code
https://storage.googleapis.com/nobletreasures/index.html
Verify that all images load correctly on the page. If not, check the following:

Ensure the URLs are correctly specified.
Verify that the objects have the correct public read permissions.
5. Troubleshooting
No Access to Images: If images aren't appearing, double-check that you set the read permissions correctly using:

bash
Copy code
gsutil acl get gs://nobletreasures/images/DIOR\ OUD\ ISPAHAN.jpeg
Invalid URL Encoding: Check that spaces in filenames are replaced with %20.

Incorrect Permissions: To inspect bucket-level permissions, use:

bash
Copy code
gsutil iam get gs://nobletreasures
Ensure allUsers has objectViewer access.

Unable to Upload: Ensure you're logged in with the correct permissions (Admin/Owner role) in Google Cloud and the bucket name is correct.

6. Conclusion
You have successfully deployed the Noble Treasures static website on Google Cloud Storage. Your website files, including images, are now publicly accessible. Use Google Cloud Storage to manage and host your content in a scalable and cost-effective manner.

Next steps may include configuring your own domain and implementing Google Cloud CDN for faster delivery.

7. License
This project is licensed under the MIT License - see the LICENSE file for details.

Feel free to fork this repository or contact me for any clarifications or adjustments.

vbnet
Copy code

---

### Key Points Included:
1. **Step-by-Step Setup**: Details for creating a Google Cloud project, enabling storage APIs, creating the bucket, and uploading website files.
2. **Permissions Management**: How to set public read access on the Cloud Storage files and buckets.
3. **HTML Modification**: Guidance on updating your HTML files to use publicly accessible URLs for images.
4. **Testing and Troubleshooting**: Ways to ensure the website loads properly and troubleshooting common issues.
5. **Conclusion & License**: Final thoughts on hosting a static site on Google Cloud Storage with additional next steps for future enhancements.

Let me know if anything else needs adjustment!





