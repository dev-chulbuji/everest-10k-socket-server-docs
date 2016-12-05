# 10K SOCKET SERVER DOSC

### SOCKET PROTOCOL

##### IP: `http://{goqual core api server sub domain}`
##### PORT: `1987`


#### REQ PROTOCOL
|WHEN | PROTOCOL |
|---- | --------|
| CONNECTION | `connection` |
| JOIN REQ | `10K_SOCKET_JOIN` |
| OPERATION SWITCH STATE | `10K_SOCKET_OPERATION` |

#### RES PROTOCOL
| WHEN | PROTOCOL |
| ---- | ---- |
| JOIN RES | `10K_SOCKET_JOIN_RES` |
| OPERATION SWITCH STATE | `10K_SOCKET_OPERATION_RES` |
---

#### SOCKET RES CODE
socket 통신의 결과 code; 200이 아닌 경우 request client에만 res, 200인 경우 room에 속해 있는 client들에게 broadcast

| CODE | DESCRIPTION |
| ---- | ---- |
| 200 | SUCCESS |
| 400 | BAD_REQUEST |
| 401 | UNAUTHORIZED |
| 404 | NOT FOUND |
| 500 | SERVER ERROR |

#### SOCKET DATA
connection 후 join protocol 시 oepration group에 join할 때
```js
{
  macaddr: '{switch serial number}',
  token: '{0auth2.0 authorization token}'
}
```
switch state 제어할 때
```js
{
  macaddr: '{switch serial number}',
  token: '{0auth2.0 authorization token}'
  btn: '{몇번 째 스위치 인지}'
  operation: '{ 1: on // 0: off }'
}
```

#### ERROR
| CASE | DESCRIPTION |
| ---- | ---- |
| UNAUTHORIZED | token expire or wrong token |
| SERVER ERROR | database transaction or err message |
| SERVER ERROR (operation) | no existed switch |


