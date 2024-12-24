# Brainwave_Matrix_Intern_Task2
This project involves deploying a simple e-commerce website using Google Cloud Storage. It focuses on hosting static content, including HTML, CSS, and product images, in a public bucket for easy access. The project highlights secure, scalable cloud storage solutions for hosting static web content.

## Project Overview

The website showcases basic product information, including an image, title, price, and a "Buy Now" button. The main goal of this project was to utilize **Google Cloud Storage** to host the static content and make it publicly accessible. This project highlights the use of Google Cloud’s powerful and cost-effective solutions for hosting static content.

### Key Features:
- **Google Cloud Storage** is used to host static files, making them publicly accessible.
- The website uses a simple layout with **HTML** for structure and **CSS** for styling.
- Product images are hosted and served directly from the cloud storage bucket.
- Publicly accessible URL allows the content to be easily shared without the need for custom DNS or domain.

### Project Structure:
Brainwave_Matrix_Intern_Task2/ ├── images/ # Directory containing product images │ ├── product1.jpg # Image file for Product 1 │ ├── product2.jpg # Image file for Product 2 ├── index.html # Main HTML file containing the website structure └── style.css # CSS file for styling the website

## Steps Involved in the Deployment:

### 1. **Google Cloud Storage Bucket Creation**
   - A **Google Cloud Storage** bucket named `your-ecommerce-bucket` was created to store all static files.
   - The bucket is publicly accessible so users can view and download the files.

### 2. **Uploading the Files**
   - **index.html**: The core HTML file for the website's layout.
   - **style.css**: The stylesheet that defines the website's design and layout.
   - **Images**: Product images that will be displayed on the website.

### 3. **Configuring Public Access**
   - Google Cloud IAM roles were set to allow public access to the objects in the bucket.
   - The necessary permissions were configured to allow **allUsers** to view the content.

### 4. **Testing and Validation**
   - Verified that the website was accessible via the public URL provided by **Google Cloud Storage**.
   - Ensured all content, including HTML, CSS, and images, loaded correctly.

### 5. **Conclusion**
   - This project showcases how **Google Cloud Storage** can be utilized to host static websites easily and securely, with public access for web hosting.
   - It demonstrates how cloud storage solutions can scale and provide easy access to static content, eliminating the need for complex server-based deployments.

## How to Access the Website
   The website is publicly hosted and can be accessed via the following URL format, where `your-ecommerce-bucket` is the name of the cloud bucket:
   
http://your-ecommerce-bucket.storage.googleapis.com/index.html

### Instructions for Running Locally:
If you'd like to preview the project locally, follow the steps below:

Clone this repository: git clone https://github.com/ganeshchelluri7/Brainwave_Matrix_Intern_Task2.git

Open index.html in a web browser: Double-click on index.html to view the e-commerce website.

## Technologies Used:
- **Google Cloud Storage**: Used for hosting static web content (HTML, CSS, images).
- **HTML**: For the structure of the web page.
- **CSS**: For styling and layout.
- **GitHub**: To manage and version control the project.

## Future Enhancements:
- Integration of backend technologies for functionality like user authentication or a shopping cart.
- Design enhancements to improve responsiveness for mobile and tablet views.
- Ability to process user orders and integrate with a payment system for a fully functional e-commerce platform.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

### Acknowledgements:
- Special thanks to **Google Cloud** for providing scalable cloud storage solutions
