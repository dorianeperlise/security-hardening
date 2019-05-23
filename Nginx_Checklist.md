# Nginx
- [ ] Ensure `server_tokens` directive is set to `off`
  - **Audit**: Run the following to verify this header is implemented on your site: `curl -I 127.0.0.1 | grep -i server`.
  
    The output should not contain the server header providing your server version, such as `Server: nginx/1.14.0`.
    
  - **Remediation**: To disable the `server_tokens` directive, set it to `off` inside a server block in your `nginx.conf`:
  ```
  server {
    ...
    server_tokens off;
    ...
  }
  ```

- [ ] Ensure `X-Frame-Options` header is configured and enabled
  - **Audit**: Run this command to verify the X-Content-Type-Options Header is enabled and set to not allow content type 
  sniffing:`grep -ir X-Frame-Options /etc/nginx`.
  
  The output should look similar to the below, but customized to your use case.
  
  ``` add_header X-Frame-Options "SAMEORIGIN"; ```
  
  - **Remediation**: Add the below to your server blocks in your nginx configuration.
  
  ``` add_header X-Frame-Options "SAMEORIGIN"; ```
  
- [ ] Ensure `X-Content-Type-Options` header is configured and enabled
  - **Audit**: 
  