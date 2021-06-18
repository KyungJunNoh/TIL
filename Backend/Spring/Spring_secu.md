# Spring_Security

```java
@Value("${spring.jwt.secret}")
private String SECRET_KEY;
```
@Value : key.yml(설정파일) 에 미리 key값을 명시해두고 어노테이션을 활용하여 값을 사용한다.

```java
spring:
  # JWT key 설정
  jwt:
    secret: KimdddsIdDidkSidjdpSJd937sdjdfjKJFudDjksdfdfi435k34tjHDKHd8iudsfFHkf8D8fKF9FDkl43ewlsdaf8dsafjk23KDF99dfF8fd6FDjDFasdfkkweqrk89DFuhsdfklsdaf98sdf98FDS89dfsjkHJK98DS98KFHD
```
ex) key.yml

---
```java
private Key getSigningKey(String secretKey) {
    byte[] keyBytes = secretKey.getBytes(StandardCharsets.UTF_8);
    return Keys.hmacShaKeyFor(keyBytes);
}
```
secretKey 파라미터에 위에 선언한 SECRET_KEY를 삽입하여 키를 **UTF-8로 인코딩** -> 왜 인코딩시키지..?   
(나중에 doGenerateToken 메소드에서 jwt토큰을 생성할때 사용)

```
디코딩 : 우리가 알아볼 수 있는 언어 (String) -> 기계어 (컴퓨터가 알아볼 수 있는 언어)   
인코딩 : 기계어 (컴퓨터가 알아볼 수 있는 언어) -> 우리가 알아볼 수 있는 언어 (String)
```

---

```java
public Claims extractAllClaims(String token) throws ExpiredJwtException {
    return Jwts.parserBuilder()
            .setSigningKey(getSigningKey(SECRET_KEY))
            .build()
            .parseClaimsJws(token)
            .getBody();
}
```
Claim정보를 가져오는 메소드
```
클레임이란?
-> JWT Header.Payload.Signature 중 Payload 에 토큰에서 사용할 정보의 조각들로 사용이 된다. Json(key/Value) 형태로 정보를 넣을 수 있다.
```
- 등록된 클레임(Registered Claim)   
등록된 클레임은 토큰 정보를 표현하기 위해 이미 정해진 종류의 데이터들로, 모두 선택적으로 작성이 가능하며 사용할 것을 권장한다.

---

```java
public Boolean isTokenExpired(String token) {
    final Date expiration = extractAllClaims(token).getExpiration();
    return expiration.before(new Date());
}
```
토큰 만료 체크 메소드

---

```java
// accessToken 생성 (dogenerateToken메소드를 사용하는 메소드)
public String generateToken(Member member) {
    return doGenerateToken(member.getMemberEmail(), member.getRoles(), member.getMemberClassNumber(), TOKEN_VALIDATION_SECOND);
}
// refreshToken 생성 (dogenerateToken메소드를 사용하는 메소드)
public String generateRefreshToken(Member member) {
    return doGenerateToken(member.getMemberEmail(), member.getRoles(), member.getMemberClassNumber(), REFRESH_TOKEN_VALIDATION_SECOND);
}
```
토큰 생성 메소드 (doGenerateToken 메소드 사용) 
- accessToken(JWT) : accessToken은 JWT이며 accessToken의 인증 방식의 문제는 만일 제 3자에게 탈취당할 경우 **보안에 취약**하다는 점이다.   
유효기간이 짧은 Token의 경우 그만큼 사용자는 로그인을 자주 해야해서 새롭게 Token의 경우 그만큼 사용자는 로그인을 자주 해서 새롭게 Token을 발급 받아야 하므로 불편하다.   
그러나 유효기간을 늘리자면, 토큰을 탈취당했을 때 보안에 더 취약해지게 된다.

- refreshToken : accessToken과 똑같은 형태의 JWT이다.    
처음에 로그인을 완료했을 때 Access Token과 동시에 발급되는 Refresh Token은 긴 유효기간을 가지면서,   
**Access Token이 만료됐을 때 새로 발급해주는 열쇠**가 된다.(여기서 만료라는 개념은 그냥 유효기간을 지났다는 의미이다.)

- (정리 : accessToken 한개의 accessToken을 계속 로그인 하는데에 사용했을때 제 3자에게 탈취당할 위험이 높다.   
그래서 refreshToken을 이용해서 일정 시간동안 계속 바꿔줘서 보안을 높이는 방법이다.)

---

```java
public String doGenerateToken(String userEmail, List<String> roles, String classNumber, long expireTime) {

    Claims claims = Jwts.claims(); // Claims 생성
    claims.put("userEmail", userEmail); //Claims 에 userEmail 삽입
    claims.put("classNumber", classNumber); //Claims 에 classNumber 삽입
    claims.put("roles", roles);

    String jwt = Jwts.builder()
            .setClaims(claims)
            .setIssuedAt(new Date(System.currentTimeMillis()))
            .setExpiration(new Date(System.currentTimeMillis() + expireTime))
            .signWith(getSigningKey(SECRET_KEY), SignatureAlgorithm.HS256)
            .compact();
    return jwt;
}
```
토큰에 Claims을 삽입하여 실질적인 토큰을 만드는 메소드

---

```java
public Boolean validateToken(String token, UserDetails userDetails) {
    final String username = getUserEmail(token);

    return (username.equals(userDetails.getUsername()) && !isTokenExpired(token));
}
```
토큰을 인증하는 메소드
- 이 과정에서 토큰이 만료가 되었는지, 토큰안에있는 회원정보와 로그인되어있는 회원정보가 같은지 비교