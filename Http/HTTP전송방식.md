1. 단순전송 - content-length를 알아야 쓸 수 있다
> 한번에 전송하고 한번에 받는다
2. 압축전송
> gzip같은걸 이용하여 압축을해서 전송한다. 크기가 많이 줄어들고 Content-Encoding이 추가로 넣어줘야함
3. 분할전송 
> Transfer-Encoding:chunked (덩어리째로 보낸다는 의미) / Contetn-length를 보내면 안됨.
4. 범위전송
> Content-Range 를 이용하여 범위를 나누어 전송한다.
