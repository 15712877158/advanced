# 浏览器缓存

浏览器缓存是浏览器对之前请求过的文件进行缓存以便下次访问时重复使用，节省宽带，提高访问速度，降低服务器压力

HTTP缓存机制主要在HTTP响应头中设定，响应头中相关字段为Expires、Cache-control、
Last-Modiified、Etag

缓存的数据在第一次请求到资源后，然后根据返回的信息来告诉如何缓存资源
可能采用强制缓存或协商缓存，这都需要根据响应的header来决定

浏览器在请求某一资源，会优先获取该资源缓存的header信息，判断是否命中强制缓存
（Pragma、Cache-control和Expires），若命中直接从缓存中获取资源（包括缓存header信息），本次请求就避免了和服务器
    
    Pragma ==>> Cache-control ==>> Expires  (优先级由高到低)

    Pragma 有唯一值 no-cache （不使用强缓存）

    Cache-control 

    Expires 是时间值，跟系统时间比较，系统时间早于Expires（强制缓存）；因系统时间可修

    改不严格
    

如果没有命中强缓存，浏览器会发送请求到服务器，请求会携带返回的有关缓存的header字段信息
（Last-Modified/If-Modified和Etag/If-None-Match）

    Etag/If-None-Match

    Etag是资源标识符，服务器端文件资源修改，Etag的hash值也会变；
    当命中协商缓存时，浏览器第二次加载时，将获取的Etag放到请求头If-None-Match中，在服务端对比hash变化。如果相等则返回304，加载浏览器缓存

    Last-Modified/If-Modified-Since

    Last-Modified/If-Modified-Since 的值代表的是文件的最后修改时间，第一次请求服务端会把资源的最后修改时间放到 Last-Modified 响应头中，第二次发起请求的时候，请求头会带上上一次响应头中的 Last-Modified 的时间，并放到 If-Modified-Since 请求头属性中，服务端根据文件最后一次修改时间和 If-Modified-Since 的值进行比较，如果相等，返回 304 ，并加载浏览器缓存。


