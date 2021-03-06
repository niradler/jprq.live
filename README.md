# jprq.live

`github.com/azimjohn/jprq.live/jprq`

- [Overview](#pkg-overview)
- [Index](#pkg-index)

## <a name="pkg-overview">Overview</a>

<img width="100%" src="https://i.imgur.com/1kXPzyd.png">

## <a name="pkg-index">Index</a>

- [type Jprq](#Jprq)
  - [func New(baseHost string) Jprq](#New)
  - [func (j *Jprq) AddTunnel(username string, port int, conn *websocket.Conn) Tunnel](#Jprq.AddTunnel)
  - [func (j \*Jprq) DeleteTunnel(host string)](#Jprq.DeleteTunnel)
  - [func (j Jprq) GetTunnelByHost(host string) (Tunnel, error)](#Jprq.GetTunnelByHost)
  - [func (j Jprq) HttpHandler(writer http.ResponseWriter, request \*http.Request)](#Jprq.HttpHandler)
  - [func (j Jprq) WebsocketHandler(w http.ResponseWriter, r \*http.Request)](#Jprq.WebsocketHandler)
- [type RequestMessage](#RequestMessage)
  - [func FromHttpRequest(httpRequest \*http.Request) RequestMessage](#FromHttpRequest)
- [type ResponseMessage](#ResponseMessage)
  - [func (responseMessage ResponseMessage) WriteToHttpResponse(writer http.ResponseWriter)](#ResponseMessage.WriteToHttpResponse)
- [type Tunnel](#Tunnel)
  - [func (tunnel Tunnel) DispatchRequests()](#Tunnel.DispatchRequests)
  - [func (tunnel Tunnel) DispatchResponses()](#Tunnel.DispatchResponses)
- [type TunnelMessage](#TunnelMessage)

#### <a name="pkg-files">Package files</a>

[http.go](/src/target/http.go) [jprq.go](/src/target/jprq.go) [messages.go](/src/target/messages.go) [tunnel.go](/src/target/tunnel.go) [utils.go](/src/target/utils.go) [websocket.go](/src/target/websocket.go)

## <a name="Jprq">type</a> [Jprq](/src/target/jprq.go?s=14:78#L3)

```go
type Jprq struct {
    // contains unexported fields
}

```

### <a name="New">func</a> [New](/src/target/jprq.go?s=80:110#L8)

```go
func New(baseHost string) Jprq
```

### <a name="Jprq.AddTunnel">func</a> (\*Jprq) [AddTunnel](/src/target/tunnel.go?s=592:672#L32)

```go
func (j *Jprq) AddTunnel(username string, port int, conn *websocket.Conn) Tunnel
```

### <a name="Jprq.DeleteTunnel">func</a> (\*Jprq) [DeleteTunnel](/src/target/tunnel.go?s=1222:1262#L55)

```go
func (j *Jprq) DeleteTunnel(host string)
```

### <a name="Jprq.GetTunnelByHost">func</a> (Jprq) [GetTunnelByHost](/src/target/tunnel.go?s=426:484#L23)

```go
func (j Jprq) GetTunnelByHost(host string) (Tunnel, error)
```

### <a name="Jprq.HttpHandler">func</a> (Jprq) [HttpHandler](/src/target/http.go?s=38:114#L7)

```go
func (j Jprq) HttpHandler(writer http.ResponseWriter, request *http.Request)
```

### <a name="Jprq.WebsocketHandler">func</a> (Jprq) [WebsocketHandler](/src/target/websocket.go?s=287:357#L20)

```go
func (j Jprq) WebsocketHandler(w http.ResponseWriter, r *http.Request)
```

## <a name="RequestMessage">type</a> [RequestMessage](/src/target/messages.go?s=232:554#L18)

```go
type RequestMessage struct {
    ID           uuid.UUID            `json:"id"`
    Method       string               `json:"method"`
    URL          string               `json:"url"`
    Body         string               `json:"body"`
    Header       map[string]string    `json:"header"`
    ResponseChan chan ResponseMessage `json:"-"`
}

```

### <a name="FromHttpRequest">func</a> [FromHttpRequest](/src/target/messages.go?s=815:877#L35)

```go
func FromHttpRequest(httpRequest *http.Request) RequestMessage
```

## <a name="ResponseMessage">type</a> [ResponseMessage](/src/target/messages.go?s=556:813#L27)

```go
type ResponseMessage struct {
    RequestId uuid.UUID         `json:"request_id"`
    Token     string            `json:"token"`
    Body      string            `json:"body"`
    Status    int               `json:"status"`
    Header    map[string]string `json:"header"`
}

```

### <a name="ResponseMessage.WriteToHttpResponse">func</a> (ResponseMessage) [WriteToHttpResponse](/src/target/messages.go?s=1421:1507#L56)

```go
func (responseMessage ResponseMessage) WriteToHttpResponse(writer http.ResponseWriter)
```

## <a name="Tunnel">type</a> [Tunnel](/src/target/tunnel.go?s=200:424#L13)

```go
type Tunnel struct {
    // contains filtered or unexported fields
}

```

### <a name="Tunnel.DispatchRequests">func</a> (Tunnel) [DispatchRequests](/src/target/tunnel.go?s=1437:1476#L66)

```go
func (tunnel Tunnel) DispatchRequests()
```

### <a name="Tunnel.DispatchResponses">func</a> (Tunnel) [DispatchResponses](/src/target/tunnel.go?s=1765:1805#L80)

```go
func (tunnel Tunnel) DispatchResponses()
```

## <a name="TunnelMessage">type</a> [TunnelMessage](/src/target/messages.go?s=144:230#L13)

```go
type TunnelMessage struct {
    Host  string `json:"host"`
    Token string `json:"token"`
}

```

---

Generated by [godoc2md](http://godoc.org/github.com/davecheney/godoc2md)
