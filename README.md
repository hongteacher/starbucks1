# Starbucks
[![스타벅스이미지](https://hongteacher.github.io/starbucks/images/starbucks_logo.png)](https://hongteacher.github.io/starbucks1/)


## Favicon(파비콘, favorites icon)
웹페이지를 나타내는 아이콘, 웹페이지의 로고를 설정합니다.  
대부분의 경우 루트 경로에 `favicon.ico` 파일을 위치하면 자동으로  
로딩하기 때문에 `<link />` 를 작성할 필요가 없습니다.  
`favicon.png` 파일을 사용하려면 다음과 같이 `<link />`를 작성하세요.
```html
<link rel="shortcut icon" href="favicon.ico" /> 
<link rel="icon" href="./favicon.png" />
```
favicon.ico 64 x 64 (px) 또는 32 x 32 또는 16 x 16  
favicon.png 500 x 500 (px)

## Reset.css
> 각 브라우저의 기본 스타일을 초기화합니다.  
[jsdelivr이동](https://www.jsdelivr.com/package/npm/the-new-css-reset)
```hmtl
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/reset-css@5.0.1/reset.min.css" />
```
## 오픈 그래프(The Open Graph protocol)
웹페이지가 소셜 미디어(페이스북 등)로 공유될 때 우선적으로 활용되는 정보를 지정합니다.  
[더 많은 오픈그래프 속성 보기](https://ogp.me/)
```
og:type: 페이지의 유형(E.g, website, video.movie)
og:site_name: 속한 사이트의 이름
og:title: 페이지의 이름(제목)
og:description: 페이지의 간단한 설명
og:image: 페이지의 대표 이미지 주소(URL)
og:url: 페이지 주소(URL)
```

## Youtube API
IFrame Player API를 통해 YouTube 동영상을 제어할 수 있습니다.  

유튜브 영상이 출력될 위치에 요소를 지정(생성)합니다.  
```html
<!-- in HEAD -->
<script defer src="./js/youtube.js"></script>

<!-- in BODY -->
<div id="player"></div>
```
onYouTubePlayerAPIReady 함수 이름은 Youtube IFrame Player API에서 사용하는 이름이기 때문에 다르게 지정하면 동작하지 않습니다!  
그리고 함수는 전역(Global) 등록해야 합니다!  

플레이어 매개변수(playerVars)에서 더 많은 옵션을 확인할 수 있습니다.  
```javascript
// Youtube IFrame API를 비동기로 로드합니다.
var tag = document.createElement('script');
tag.src = "https://www.youtube.com/iframe_api";
var firstScriptTag = document.getElementsByTagName('script')[0];
firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

function onYouTubePlayerAPIReady() {
  // <div id="player"></div>
  new YT.Player('player', {
    videoId: 'An6LvWQuj_8', // 재생할 유튜브 영상 ID
    playerVars: {
      autoplay: true, // 자동 재생 유무
      loop: true, // 반복 재생 유무
      playlist: 'An6LvWQuj_8' // 반복 재생할 유튜브 영상 ID 목록
    },
    events: {
      // 영상이 준비되었을 때,
      onReady: function (event) {
        event.target.mute(); // 음소거!
      }
    }
  });
}
```

