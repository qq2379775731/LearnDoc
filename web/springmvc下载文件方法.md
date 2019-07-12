### 标题

springmvc文件下载

---

### 时间

2019-5-10

---

### 内容

```java
@RequestMapping(value="download")
    public ResponseEntity<byte[]> download(HttpSession session, String fileName) throws IOException {
        String downloadFilePath = session.getServletContext().getRealPath("/homeworks");   //获取存储文件路径
        File file = new File(downloadFilePath + File.separator + fileName);  //下载的文件
        HttpHeaders httpHeaders = new HttpHeaders();  //http头部信息
        String downloadFileName = fileName;
        httpHeaders.setContentDispositionFormData("attachment", downloadFileName);  //设置下载文件名
        httpHeaders.setContentType(MediaType.APPLICATION_OCTET_STREAM);				//设置http返回类型
        //MediaType:互联网媒介类型  contentType：具体请求中的媒体类型信息
        return new ResponseEntity<>(FileUtils.readFileToByteArray(file), httpHeaders, HttpStatus.CREATED);
    }
```

---

### 注释



---

### 获取路径



---

### 其他



------

