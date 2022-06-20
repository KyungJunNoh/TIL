# oEmbed
최근 oEmbed에 대해 공부할 일이 생겨서 공부를 하게 되었다.

### oEmbed 란?
- oEmbed는 다른 사이트의 URL을 내장된 표현(사진, 영상 등의 정보)을 가능하게 하는 Format 이다.
- 유저가 Resource 에 해당하는 링크를 입력할 때, 웹사이트들이 Resource 를 직접 파싱하지 않고, 내장된 컨텐츠(사진, 영상 등의 정보)를 보여줄 수 있게 하는 간단한 API 이다.
- oEmbed는 2008년 Slack의 공동 창업자인 Cal Henderson 이 제안한 Open Format 이다.
- 공식적인 Format은 아니지만 영향력 있는 서비스들( ex: Youtube, Facebook, Slideshare, Workpress 등) 이 참여하여 상당히 대중화 되었다.

### oEmbed 사용 예시
사용자가 아래와 같은 HTTP Request 를 생성하면
```
http://www.youtube.com/oembed?url=https://www.youtube.com/watch?v=i7muqI90138&list=RDi7muqI90138&start_radio=1
```
Youtube는 아래와 같은 oEmbed Response를 돌려준다.

```json
{
  "title": "창모 (CHANGMO) - 널 지워야해 (Erase You) (Prod by. CHANGMO) [널 지워야해]│가사, Lyrics",
  "author_name": "리릭뭉치",
  "author_url": "https://www.youtube.com/channel/UC9Vqr5Eax-P92HKtljIsW0g",
  "type": "video",
  "height": 113,
  "width": 200,
  "version": "1.0",
  "provider_name": "YouTube",
  "provider_url": "https://www.youtube.com/",
  "thumbnail_height": 360,
  "thumbnail_width": 480,
  "thumbnail_url": "https://i.ytimg.com/vi/i7muqI90138/hqdefault.jpg",
  "html": "<iframe width=\"200\" height=\"113\" src=\"https://www.youtube.com/embed/i7muqI90138?feature=oembed\" frameborder=\"0\" allow=\"accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture\" allowfullscreen title=\"창모 (CHANGMO) - 널 지워야해 (Erase You) (Prod by. CHANGMO) [널 지워야해]│가사, Lyrics\"></iframe>"
}
```

이는 URL 을 사용자가 웹사이트에 동영상을 넣을 수 있게(공유 받을 수 있게) 구조화 된 데이터로 바꾸어주는 것이다.

### oEmbed 를 공부하며
- 디스코드나 노션에서 임베드를 사용하는것을 보았는데 이것도 oEmbed 일까..?
- 자료가 부족하여 공부하는데에 어려움이 있었지만, 공부하고보니 어렵지 않은 내용이였던 것 같다.

### oEmbed 를 공부한 자료
- https://oembed.com/ (oEmbed 공식 사이트)