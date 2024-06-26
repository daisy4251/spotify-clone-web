# 230113-230114 Spotify 클론 코딩

[Spotify 클론 코딩 페이지](https://bejewelled-sprinkles-a7620b.netlify.app/)

## 1. CSS 구조 파악

![구조 파악](./image/image.png)

## 2. CSS 구조 정하기

![구조 정하기](./image/image-1.png)

## 3. 완료 모습

![완료 초기](./image/image-2.png)
![모바일구현](https://github.com/daisy4251/spotify-clone-web/assets/165018586/81ca617c-a81a-4088-bd26-12615c6d3a18)

---

### sidebar mobile처리

- input, label을 이용한 input:checked lable transition 처리
- 근접 요소 선택자 '+' 사용

```css
/* input */
header #mobile-btn {
	display: none;
}

/* input 옆에 label */
header #mobile-btn + .mobile-icon {
	display: none;
	margin: 30px;
	width: 24px;
	height: 20px;
	position: absolute;
	top: 0;
	right: 0;
	z-index: 1;
	cursor: pointer;
}

header #mobile-btn + .mobile-icon span {
	display: block;
	position: absolute;
	width: 100%;
	height: 2px;
	border-radius: 24px;
	background: #fff;
	transition: all 0.35s;
}

header #mobile-btn + .mobile-icon span:nth-child(1) {
	top: 0;
}

header #mobile-btn + .mobile-icon span:nth-child(2) {
	top: 50%;
	transform: translateY(-50%);
}

header #mobile-btn + .mobile-icon span:nth-child(3) {
	bottom: 0;
}

/* input:checked 상태일 때 */

header #mobile-btn:checked + .mobile-icon span:nth-child(1) {
	top: 50%;
	transform: translateY(-50%) rotate(45deg);
}
header #mobile-btn:checked + .mobile-icon span:nth-child(2) {
	opacity: 0;
}
header #mobile-btn:checked + .mobile-icon span:nth-child(3) {
	bottom: 50%;
	transform: translateY(50%) rotate(-45deg);
}

/* div-모바일 메뉴 */

header .side-bar {
	width: 100%;
	position: absolute;
	top: 80px;
	left: -9999px;
	padding: 1.2em;
	background-color: #000;
	transition: all 0.35s;
}

/* input:checked 상태일 때 */

header #mobile-btn:checked + .mobile-icon + .side-bar {
	left: 0;
}

header .side-bar li {
	line-height: 3em;
}
```

### 미디어 쿼리를 이용한 큰 화면 구현 시 깨짐 수정

- min-width: 2048px

```css
@media (min-width: 2048px) {
	body {
		font-size: 1.2em;
	}

	.inner {
		width: 80%;
	}

	main .content {
		width: 95%;
	}

	main .content h2 {
		font-size: 10em;
	}
	main .text p {
		font-size: 1.5em;
	}
}
```

### 미디어 쿼리를 이용한 태블릿 및 노트북 화면 구현 시 깨짐 수정

- max-width: 1200px

```css
@media (max-width: 1200px) {
	main .content h2 {
		font-size: 8em;
	}
}
```

- max-width: 992px

```css
@media (max-width: 992px) {
	main .content h2 {
		font-size: 6em;
	}

	footer .section-menu {
		flex-direction: column;
		align-items: center;
	}

	footer .section-menu .menu-area {
		margin-bottom: 50px;
	}

	footer .section-privacy {
		flex-direction: column;
		align-items: center;
		gap: 20px;
	}

	footer .section-privacy .privacy-area {
		text-align: center;
	}
}
```

### 미디어 쿼리를 이용한 모바일 구현 시 깨짐 수정

- 초기 구현은
  [Replit](https://832a1242-7671-4884-b440-953d3ffddc3d-00-zesjd9c8otxa.pike.repl.co/) 또는
  [Notion](https://teal-catcher-309.notion.site/230113-230114-Spotify-1a9420e4cd39472085d2de9721e8877b) 참조

- max-width: 768px

```css
@media (max-width: 768px) {
	header .nav a,
	header .nav span {
		display: none;
	}

	header #mobile-btn + .mobile-icon {
		display: block;
	}

	main .content h2 {
		font-size: 4.5em;
	}

	main .mobile-btn:hover .mobile-nav {
		display: block;
	}

	footer .section-menu {
		flex-direction: column;
		align-items: center;
		/* justify-content: center; */
	}

	footer .section-menu .menu-area {
		flex-direction: column;
		justify-content: center;
		align-items: center;
		gap: 0.8em;
	}

	footer .section-menu .menu-area .flex-column {
		justify-content: center;
		align-items: center;
		text-align: center;
	}

	footer .section-menu .menu-area .flex-column li h3 {
		color: #fff;
		cursor: pointer;
	}

	footer .section-menu .menu-area .flex-column li h3::after {
		display: inline-block;
		width: 15px;
		height: 15px;
		line-height: 0.8em;
		border-radius: 100%;
		text-align: center;
		content: '+';
		margin-left: 0.5em;
		border: 1px solid #fff;
		padding: 0.5em;
	}

	footer .section-menu .menu-area .flex-column li h3:hover {
		color: #1ed760;
	}

	footer .section-menu .menu-area .flex-column li:hover h3::after {
		border-color: #1ed760;
	}

	footer .section-privacy .privacy-area {
		margin-bottom: 2em;
	}
}
```

- max-width: 576px

```css
@media (max-width: 576px) {
	main .content h2 {
		font-size: 4em;
	}

	footer .section-menu .menu-area .flex-column li h3 {
		color: #fff;
		cursor: pointer;
		font-size: 1em;
	}

	footer .section-menu .menu-area .flex-column li h3::after {
		width: 10px;
		height: 10px;
		line-height: 0.8em;
	}

	footer .section-menu .menu-area .flex-column li a {
		display: none;
	}

	footer .section-usa {
		text-align: center;
	}

	footer .section-privacy p {
		text-align: center;
	}

	footer .section-privacy .privacy-area {
		display: none;
	}

	footer .section-privacy p {
		font-size: 0.9em;
	}
}
```

- max-width: 472px

```css
@media (max-width: 472px) {
	main .content h2 {
		font-size: 3em;
	}

	main .text {
		font-size: 1em;
	}

	footer .section-menu .menu-area .flex-column li h3 {
		color: #fff;
		cursor: pointer;
		font-size: 0.8em;
	}
}

@media (max-width: 356px) {
	main .content h2 {
		font-size: 2.5em;
	}

	main .button-area button {
		font-size: 0.8em;
	}
}
```

### Spotify Fonts

- Spotify Fonts(spotify-circular) 사용

```css
body {
	font-family: spotify-circular, Helvetica, Arial, sans-serif;
}
```

### Favicon

- 스포티파이 제공 favicon 사용

```html
<!-- FAVICON -->
<link rel="icon" href="https://open.spotifycdn.com/cdn/images/favicon32.b64ecc03.png" />
```

### Icon

- 무난한 [Font Awsome](https://fontawesome.com/) 사용
