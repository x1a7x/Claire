



This is a total, 100 percent overhaul of Claire. 


This application is a simple yet powerful imageboard designed specifically for chess discussions. It allows users to create threads, post messages, and share images or videos (specifically mp4 files) related to chess. The application is built with security and user experience in mind, making it suitable for deployment on a production chess discussion site.

The imageboard is developed using PHP and SQLite, ensuring a lightweight and efficient setup. It uses a single index.php file for all its functionalities, making it easy to deploy and manage. The design focuses on simplicity and responsiveness, providing a seamless experience across both desktop and mobile devices.

Installation and Setup

To get started with the imageboard, you need a server running Ubuntu 24.04 or a similar Linux distribution. Ensure that you have PHP installed with the necessary extensions, including SQLite support. You will also need to install ImageMagick and FFmpeg, which are required for validating and processing uploaded images and videos. These can be installed using the apt package manager with the commands sudo apt install imagemagick and sudo apt install ffmpeg.

Place the index.php and style.css files in your web server's document root or the desired directory where you want the imageboard to reside. Create an index.html file at the root of your website to serve as a welcome page, listing the different boards or providing introductory information about your site.

Ensure that the uploads/ directory exists and is writable by the web server. The application uses this directory to store uploaded files securely. If the directory does not exist, the script will attempt to create it with the appropriate permissions.

Configuration

Open the index.php file to adjust configuration settings as needed. At the top of the file, you'll find a $board_title variable, which you can set to your desired board name, such as 'Chess Discussion Board'. This title will appear on the main page and reply pages, providing a consistent branding for your imageboard.

Adjust your PHP configuration (php.ini) to ensure that it allows file uploads up to 20MB, matching your desired maximum file size for uploads. Set upload_max_filesize and post_max_size to at least 20M. Restart your web server after making changes to the PHP configuration to apply the new settings.

In your Nginx configuration, set the client_max_body_size directive to 20M within your server block. This setting prevents users from uploading files larger than 20MB, providing an initial layer of protection against oversized uploads. Reload Nginx to apply the changes after modifying the configuration.

Usage

Users can access the imageboard by navigating to the URL where you've placed the index.php file. On the main board page, users can create new threads by posting messages and optionally uploading images or mp4 videos. The simplified posting form includes a resizable message textarea and a file upload field, making it straightforward for users to contribute content.

Each thread displays the name "Anonymous" on the top-left and a reply button with a reply count on the top-right. Uploaded images and videos are displayed centered under the header, followed by the message text. Users can click on the reply button to view the thread in reply mode, where they can see all replies in chronological order and post their own replies using the same simplified form.

The application enforces a maximum upload size of 20MB for both images and videos. If a user attempts to upload a file exceeding this limit, the application displays an error message informing them that the file size exceeds the allowed limit. This ensures that the server's resources are protected and that users are aware of the upload restrictions.

Security Considerations

The application incorporates several security measures to ensure safe operation in a production environment. It uses CSRF tokens in forms to protect against cross-site request forgery attacks and sanitizes all user inputs using htmlspecialchars() to prevent cross-site scripting (XSS) attacks. Prepared statements are employed for database interactions to safeguard against SQL injection.

File uploads are handled with care, using both ImageMagick and FFmpeg to validate and process images and videos securely. These tools check for corrupted or malicious files, ensuring that only valid images and mp4 videos are accepted. The application restricts file types to jpg, jpeg, png, gif, webp, and mp4, explicitly excluding unsafe file types such as svg or executable files.

The uploads/ directory stores files with unique filenames, preventing overwriting and obscuring original filenames. It's important to configure your web server to prevent script execution in the uploads directory, adding an extra layer of security. Serving the site over HTTPS using SSL/TLS certificates, such as those provided by Let's Encrypt, is recommended to encrypt data transmission and enhance security.

Final Thoughts

This imageboard application offers a robust platform for chess enthusiasts to discuss and share content related to chess. Its simplicity and focus on security make it an excellent choice for deployment on a production chess discussion site. By following the installation and configuration instructions, and paying close attention to the security considerations, you can provide users with a safe and enjoyable experience.

Regularly monitor and update your server and application to protect against new vulnerabilities. Keep your software dependencies up to date, and consider implementing additional security measures as needed. By maintaining vigilance and adhering to best practices, you can ensure that your chess discussion imageboard remains a valuable and secure resource for your community.
