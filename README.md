## synopsis
An Improved version of [sling](https://github.com/dghubble/sling), mainly for retry mechanism & debug info.

## New API
### Headers
```go
headers := map[string]string{
    "User-Agent": "Gophergram API Client",
    "Referer":    "http://www.baidu.com",
}
s := sling.New().Base(baseUrl).Adds(headers)
req, err := s.New().Get("gophergram/list").Request()
```
U can add more than one header k-v pair at one time.

### Retry
```go
s := sling.New().Base(baseUrl).Retry(2).SleepTime(2*time.Second)
req, err := s.New().Get("gophergram/list").Request()
```
Use `Retry()` to set retry times.
Use `SleepTime()` to set sleep time between tries.

It won't do rerty by default.
For convenience,U can use `DefaultRetry()` to set **try=3, sleep=100ms**.

### Debug
Use `Debug(true)` will print some info about req.
