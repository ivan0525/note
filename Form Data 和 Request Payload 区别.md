### Form Data 和 Request Payload 区别


1. 如果请求头里设置Content-Type: application/x-www-form-urlencoded，那么这个请求被认为是表单请求，
参数出现在Form Data里，格式为key=value&key=value&key=value...

2. 原生的AJAX请求头里设置Content-Type:application/json，或者使用默认的请求头Content-Type:text/plain;参数会显示在Request payload块里提交。
