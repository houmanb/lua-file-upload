# Lua-file-upload
File upload API based on Openresty

# Configuration
`` ``
$ Save_tempdr #: Temporary file storage directory with the same permissions as Nginx users
$ Upload_root #: File upload floor directory, permissions must be the same as Nginx users
$ Render_url #: After the file was uploaded successfully, the request URL was returned
`` ``

# Use
## use the project comes with the demo configuration to run
`` ``
$ PATH / sbin / nginx -c $ PATH / lua-file-upload / nginx.conf
`` ``

## Test API
`` ``
Curl -i http: // localhost: 8000 / api
HTTP / 1.1 200 OK
Date: Tue, 18 Oct 2016 11:20:22 GMT
Content-Type: application / json
Transfer-Encoding: chunked
Connection: keep-alive

{"Message": "Welcome Blob Service."}


#: File Upload
Curt -i -X ​​POST -H "Content-Type: multipart / form-data;" -F "path = test" -F "file = @. / Ok.txt" "http: // localhost: 8000 / api / Upload "
HTTP / 1.1 100 Continue

HTTP / 1.1 200 OK
Date: Tue, 18 Oct 2016 11:19:58 GMT
Content-Type: application / json
Transfer-Encoding: chunked
Connection: keep-alive

{"File": "ok.txt", "size": 0, "path": "coreos.me \ / test \ /ok.txt"}

#: If the file exists, replace the file
"-F" path = test "-F" force = true "-F" file = @. / Ok.txt "" http: / / Localhost: 8000 / api / upload "
HTTP / 1.1 100 Continue

HTTP / 1.1 200 OK
Date: Wed, 19 Oct 2016 02:19:41 GMT
Content-Type: application / json
Transfer-Encoding: chunked
Connection: keep-alive

{"File": "ok.txt", "size": 0, "path": "coreos.me \ / test \ /ok.txt"}
`` ``
