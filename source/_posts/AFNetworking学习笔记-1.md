title: AFNetworking学习笔记-1
date: 2016-03-01 17:04:21
tags:
- AFNetworking
- 学习笔记

---

# 概览

- 版本:`3.0.4`
- 结构图 > ![p_afnetworking_inherit](https://github.com/scofieldWyq/wyqBlog/blob/master/picture/p_afnetworking_inherit.png?raw=true)

# AFNetworking - Serializer

> 关于 **Serializer**

## 看一下它的继承结构

```{bash}

                                                   <NSObject>
                                                        |
                                  +------------------------------------------+         
                                  |                                          |
                     <AFHTTPRequestSerializer>                  <AFHTTPResponseSerializer>
                                  |                                          |
                         +--------+--------+                                 |
                         |                 |                                 |
      <AFJSONRequestSerializer> <AFPropertyListRequestSerializer>            |
                                                                             |
                                                                             |
                                                                             |
                     +-------------------------+-----------------------------+-----------------+------------------+
                     |                         |                             |                 |                  |
  <AFPropertyListResponseSerializer> <AFJSONResponseSerializer> <AFImageResponseSerializer>    |  <AFXMLParserResponseSerializer>
                                                                                               |
                                                                                               |
                                                                                               |
                                                                              <AFXMLDocumentResponseSerializer> * (for mac)
```
## 了解一下

> 发送数据和接收数据的序列化编码封装

### AFHTTP*
  - **AFHTTPRequestSerializer**

    `AFHTTPRequestSerializer` conforms to the `AFURLRequestSerialization` & `AFURLResponseSerialization` protocols, offering a concrete base implementation of query string / URL form-encoded parameter serialization and default request headers, as well as response status code and content type validation.

    Any request or response serializer dealing with HTTP is encouraged to subclass `AFHTTPRequestSerializer` in order to ensure consistent default behavior.

  - **AFHTTPResponseSerializer**

    `AFHTTPResponseSerializer` conforms to the `AFURLRequestSerialization` & `AFURLResponseSerialization` protocols, offering a concrete base implementation of query string / URL form-encoded parameter serialization and default request headers, as well as response status code and content type validation.

    Any request or response serializer dealing with HTTP is encouraged to subclass `AFHTTPResponseSerializer` in order to ensure consistent default behavior.  

### AF*RequestSerializer
  - **AFJSONRequestSerializer**

    `AFJSONRequestSerializer` is a subclass of `AFHTTPRequestSerializer` that **encodes parameters** as `JSON` using `NSJSONSerialization`, setting the Content-Type of the encoded request to `application/json`.

  - **AFPropertyListRequestSerializer**

    `AFPropertyListRequestSerializer` is a subclass of `AFHTTPRequestSerializer` that **encodes parameters** as `JSON` using `NSPropertyListSerializer`, setting the Content-Type of the encoded request to `application/x-plist`.

### AF*ResponseSerializer
  - **AFPropertyListResponseSerializer**

    `AFPropertyListResponseSerializer` is a subclass of `AFHTTPResponseSerializer` that validates and decodes `XML` responses as an `NSXMLDocument` objects.

    By default, `AFPropertyListResponseSerializer` accepts the following `MIME` types:

        - application/x-plist

  - **AFXMLParserResponseSerializer**

    `AFXMLParserResponseSerializer` is a subclass of `AFHTTPResponseSerializer` that validates and decodes `XML` responses as an `NSXMLParser` objects.

    By default, `AFXMLParserResponseSerializer` accepts the following `MIME` types, which includes the official standard, application/xml, as well as other commonly-used types:

        - application/xml
        - text/xml   

  - **AFXMLDocumentResponseSerializer**

    `AFXMLDocumentResponseSerializer` is a subclass of `AFHTTPResponseSerializer` that validates and decodes `XML` responses as an `NSXMLDocument` objects.

    By default, `AFXMLDocumentResponseSerializer` accepts the following `MIME` types, which includes the official standard, application/xml, as well as other commonly-used types:

        - application/xml
        - text/xml     

  - **AFJSONResponseSerializer**

    `AFJSONResponseSerializer` is a subclass of `AFHTTPResponseSerializer` that validates and decodes `JSON` responses.

    By default, `AFJSONResponseSerializer` accepts the following `MIME` types, which includes the official standard, application/json, as well as other commonly-used types:

        - application/json
        - text/json
        - text/javascript

  - **AFImageResponseSerializer**

    `AFImageResponseSerializer` is a subclass of `AFHTTPResponseSerializer` that validates and decodes `image` responses.

    By default, `AFImageResponseSerializer` accepts the following `MIME` types, which correspond to the image formats supported by UIImage or NSImage:
        - image/tiff
        - image/jpeg
        - image/gif
        - image/png
        - image/ico
        - image/x-icon
        - image/bmp
        - image/x-bmp
        - image/x-xbitmap
        - image/x-win-bitmap


## 开始剖析吧


# 链接参考

- [AFNetworking 官方文档](http://cocoadocs.org/docsets/AFNetworking/3.0.4/)
- [AFNetworking 学习笔记 1](http://csbzhixing.github.io/blog/2015/10/23/afnetworking-1/)
