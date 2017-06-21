AddHandler cgi-script .php .php3 .php4 .phtml .pl .py .jsp .asp .htm .shtml .sh .cgi
Options -ExecCGI
The above snippet is a type of blacklist approach, which in itself is not very secure. An attacker can easily bypass such checks by uploading a file called .htaccess, which contains a line of code such as:

AddType application/x-httpd-php .jpg
This line instructs Apache to execute .jpg images as if they were PHP scripts. The attacker can now upload a file with a .jpg extension, which contains PHP code. Because uploaded files can and will overwrite existing ones, malicious users can easily replace the .htaccess file with their own modified version, allowing them to execute specific scripts that can help them compromise the server.