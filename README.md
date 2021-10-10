<html>
	<head>
		<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
		<title>Predator and Prey simulator</title>
		<style>
			/* cspell:disable-file */
			/* webkit printing magic: print all background colors */
			html {
				-webkit-print-color-adjust: exact;
			}
			* {
				box-sizing: border-box;
				-webkit-print-color-adjust: exact;
			}

			html,
			body {
				margin: 0;
				padding: 0;
			}
			@media only screen {
				body {
					margin: 2em auto;
					max-width: 900px;
					color: rgb(55, 53, 47);
				}
			}

			body {
				line-height: 1.5;
				white-space: pre-wrap;
			}

			a,
			a.visited {
				color: inherit;
				text-decoration: underline;
			}

			.pdf-relative-link-path {
				font-size: 80%;
				color: #444;
			}

			h1,
			h2,
			h3 {
				letter-spacing: -0.01em;
				line-height: 1.2;
				font-weight: 600;
				margin-bottom: 0;
			}

			.page-title {
				font-size: 2.5rem;
				font-weight: 700;
				margin-top: 0;
				margin-bottom: 0.75em;
			}

			h1 {
				font-size: 1.875rem;
				margin-top: 1.875rem;
			}

			h2 {
				font-size: 1.5rem;
				margin-top: 1.5rem;
			}

			h3 {
				font-size: 1.25rem;
				margin-top: 1.25rem;
			}

			.source {
				border: 1px solid #ddd;
				border-radius: 3px;
				padding: 1.5em;
				word-break: break-all;
			}

			.callout {
				border-radius: 3px;
				padding: 1rem;
			}

			figure {
				margin: 1.25em 0;
				page-break-inside: avoid;
			}

			figcaption {
				opacity: 0.5;
				font-size: 85%;
				margin-top: 0.5em;
			}

			mark {
				background-color: transparent;
			}

			.indented {
				padding-left: 1.5em;
			}

			hr {
				background: transparent;
				display: block;
				width: 100%;
				height: 1px;
				visibility: visible;
				border: none;
				border-bottom: 1px solid rgba(55, 53, 47, 0.09);
			}

			img {
				max-width: 100%;
			}

			@media only print {
				img {
					max-height: 100vh;
					object-fit: contain;
				}
			}

			@page {
				margin: 1in;
			}

			.collection-content {
				font-size: 0.875rem;
			}

			.column-list {
				display: flex;
				justify-content: space-between;
			}

			.column {
				padding: 0 1em;
			}

			.column:first-child {
				padding-left: 0;
			}

			.column:last-child {
				padding-right: 0;
			}

			.table_of_contents-item {
				display: block;
				font-size: 0.875rem;
				line-height: 1.3;
				padding: 0.125rem;
			}

			.table_of_contents-indent-1 {
				margin-left: 1.5rem;
			}

			.table_of_contents-indent-2 {
				margin-left: 3rem;
			}

			.table_of_contents-indent-3 {
				margin-left: 4.5rem;
			}

			.table_of_contents-link {
				text-decoration: none;
				opacity: 0.7;
				border-bottom: 1px solid rgba(55, 53, 47, 0.18);
			}

			table,
			th,
			td {
				border: 1px solid rgba(55, 53, 47, 0.09);
				border-collapse: collapse;
			}

			table {
				border-left: none;
				border-right: none;
			}

			th,
			td {
				font-weight: normal;
				padding: 0.25em 0.5em;
				line-height: 1.5;
				min-height: 1.5em;
				text-align: left;
			}

			th {
				color: rgba(55, 53, 47, 0.6);
			}

			ol,
			ul {
				margin: 0;
				margin-block-start: 0.6em;
				margin-block-end: 0.6em;
			}

			li > ol:first-child,
			li > ul:first-child {
				margin-block-start: 0.6em;
			}

			ul > li {
				list-style: disc;
			}

			ul.to-do-list {
				text-indent: -1.7em;
			}

			ul.to-do-list > li {
				list-style: none;
			}

			.to-do-children-checked {
				text-decoration: line-through;
				opacity: 0.375;
			}

			ul.toggle > li {
				list-style: none;
			}

			ul {
				padding-inline-start: 1.7em;
			}

			ul > li {
				padding-left: 0.1em;
			}

			ol {
				padding-inline-start: 1.6em;
			}

			ol > li {
				padding-left: 0.2em;
			}

			.mono ol {
				padding-inline-start: 2em;
			}

			.mono ol > li {
				text-indent: -0.4em;
			}

			.toggle {
				padding-inline-start: 0em;
				list-style-type: none;
			}

			/* Indent toggle children */
			.toggle > li > details {
				padding-left: 1.7em;
			}

			.toggle > li > details > summary {
				margin-left: -1.1em;
			}

			.selected-value {
				display: inline-block;
				padding: 0 0.5em;
				background: rgba(206, 205, 202, 0.5);
				border-radius: 3px;
				margin-right: 0.5em;
				margin-top: 0.3em;
				margin-bottom: 0.3em;
				white-space: nowrap;
			}

			.collection-title {
				display: inline-block;
				margin-right: 1em;
			}

			time {
				opacity: 0.5;
			}

			.icon {
				display: inline-block;
				max-width: 1.2em;
				max-height: 1.2em;
				text-decoration: none;
				vertical-align: text-bottom;
				margin-right: 0.5em;
			}

			img.icon {
				border-radius: 3px;
			}

			.user-icon {
				width: 1.5em;
				height: 1.5em;
				border-radius: 100%;
				margin-right: 0.5rem;
			}

			.user-icon-inner {
				font-size: 0.8em;
			}

			.text-icon {
				border: 1px solid #000;
				text-align: center;
			}

			.page-cover-image {
				display: block;
				object-fit: cover;
				width: 100%;
				height: 30vh;
			}

			.page-header-icon {
				font-size: 3rem;
				margin-bottom: 1rem;
			}

			.page-header-icon-with-cover {
				margin-top: -0.72em;
				margin-left: 0.07em;
			}

			.page-header-icon img {
				border-radius: 3px;
			}

			.link-to-page {
				margin: 1em 0;
				padding: 0;
				border: none;
				font-weight: 500;
			}

			p > .user {
				opacity: 0.5;
			}

			td > .user,
			td > time {
				white-space: nowrap;
			}

			input[type='checkbox'] {
				transform: scale(1.5);
				margin-right: 0.6em;
				vertical-align: middle;
			}

			p {
				margin-top: 0.5em;
				margin-bottom: 0.5em;
			}

			.image {
				border: none;
				margin: 1.5em 0;
				padding: 0;
				border-radius: 0;
				text-align: center;
			}

			.code,
			code {
				background: rgba(135, 131, 120, 0.15);
				border-radius: 3px;
				padding: 0.2em 0.4em;
				border-radius: 3px;
				font-size: 85%;
				tab-size: 2;
			}

			code {
				color: #eb5757;
			}

			.code {
				padding: 1.5em 1em;
			}

			.code-wrap {
				white-space: pre-wrap;
				word-break: break-all;
			}

			.code > code {
				background: none;
				padding: 0;
				font-size: 100%;
				color: inherit;
			}

			blockquote {
				font-size: 1.25em;
				margin: 1em 0;
				padding-left: 1em;
				border-left: 3px solid rgb(55, 53, 47);
			}

			.bookmark {
				text-decoration: none;
				max-height: 8em;
				padding: 0;
				display: flex;
				width: 100%;
				align-items: stretch;
			}

			.bookmark-title {
				font-size: 0.85em;
				overflow: hidden;
				text-overflow: ellipsis;
				height: 1.75em;
				white-space: nowrap;
			}

			.bookmark-text {
				display: flex;
				flex-direction: column;
			}

			.bookmark-info {
				flex: 4 1 180px;
				padding: 12px 14px 14px;
				display: flex;
				flex-direction: column;
				justify-content: space-between;
			}

			.bookmark-image {
				width: 33%;
				flex: 1 1 180px;
				display: block;
				position: relative;
				object-fit: cover;
				border-radius: 1px;
			}

			.bookmark-description {
				color: rgba(55, 53, 47, 0.6);
				font-size: 0.75em;
				overflow: hidden;
				max-height: 4.5em;
				word-break: break-word;
			}

			.bookmark-href {
				font-size: 0.75em;
				margin-top: 0.25em;
			}

			.sans {
				font-family: ui-sans-serif, -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, 'Apple Color Emoji', Arial, sans-serif, 'Segoe UI Emoji', 'Segoe UI Symbol';
			}
			.code {
				font-family: 'SFMono-Regular', Menlo, Consolas, 'PT Mono', 'Liberation Mono', Courier, monospace;
			}
			.serif {
				font-family: Lyon-Text, Georgia, ui-serif, serif;
			}
			.mono {
				font-family: iawriter-mono, Nitti, Menlo, Courier, monospace;
			}
			.pdf .sans {
				font-family: Inter, ui-sans-serif, -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, 'Apple Color Emoji', Arial, sans-serif, 'Segoe UI Emoji', 'Segoe UI Symbol', 'Twemoji',
					'Noto Color Emoji', 'Noto Sans CJK JP';
			}
			.pdf:lang(zh-CN) .sans {
				font-family: Inter, ui-sans-serif, -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, 'Apple Color Emoji', Arial, sans-serif, 'Segoe UI Emoji', 'Segoe UI Symbol', 'Twemoji',
					'Noto Color Emoji', 'Noto Sans CJK SC';
			}
			.pdf:lang(zh-TW) .sans {
				font-family: Inter, ui-sans-serif, -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, 'Apple Color Emoji', Arial, sans-serif, 'Segoe UI Emoji', 'Segoe UI Symbol', 'Twemoji',
					'Noto Color Emoji', 'Noto Sans CJK TC';
			}
			.pdf:lang(ko-KR) .sans {
				font-family: Inter, ui-sans-serif, -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, 'Apple Color Emoji', Arial, sans-serif, 'Segoe UI Emoji', 'Segoe UI Symbol', 'Twemoji',
					'Noto Color Emoji', 'Noto Sans CJK KR';
			}
			.pdf .code {
				font-family: Source Code Pro, 'SFMono-Regular', Menlo, Consolas, 'PT Mono', 'Liberation Mono', Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK JP';
			}
			.pdf:lang(zh-CN) .code {
				font-family: Source Code Pro, 'SFMono-Regular', Menlo, Consolas, 'PT Mono', 'Liberation Mono', Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK SC';
			}
			.pdf:lang(zh-TW) .code {
				font-family: Source Code Pro, 'SFMono-Regular', Menlo, Consolas, 'PT Mono', 'Liberation Mono', Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK TC';
			}
			.pdf:lang(ko-KR) .code {
				font-family: Source Code Pro, 'SFMono-Regular', Menlo, Consolas, 'PT Mono', 'Liberation Mono', Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK KR';
			}
			.pdf .serif {
				font-family: PT Serif, Lyon-Text, Georgia, ui-serif, serif, 'Twemoji', 'Noto Color Emoji', 'Noto Serif CJK JP';
			}
			.pdf:lang(zh-CN) .serif {
				font-family: PT Serif, Lyon-Text, Georgia, ui-serif, serif, 'Twemoji', 'Noto Color Emoji', 'Noto Serif CJK SC';
			}
			.pdf:lang(zh-TW) .serif {
				font-family: PT Serif, Lyon-Text, Georgia, ui-serif, serif, 'Twemoji', 'Noto Color Emoji', 'Noto Serif CJK TC';
			}
			.pdf:lang(ko-KR) .serif {
				font-family: PT Serif, Lyon-Text, Georgia, ui-serif, serif, 'Twemoji', 'Noto Color Emoji', 'Noto Serif CJK KR';
			}
			.pdf .mono {
				font-family: PT Mono, iawriter-mono, Nitti, Menlo, Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK JP';
			}
			.pdf:lang(zh-CN) .mono {
				font-family: PT Mono, iawriter-mono, Nitti, Menlo, Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK SC';
			}
			.pdf:lang(zh-TW) .mono {
				font-family: PT Mono, iawriter-mono, Nitti, Menlo, Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK TC';
			}
			.pdf:lang(ko-KR) .mono {
				font-family: PT Mono, iawriter-mono, Nitti, Menlo, Courier, monospace, 'Twemoji', 'Noto Color Emoji', 'Noto Sans Mono CJK KR';
			}
			.highlight-default {
			}
			.highlight-gray {
				color: rgb(155, 154, 151);
			}
			.highlight-brown {
				color: rgb(100, 71, 58);
			}
			.highlight-orange {
				color: rgb(217, 115, 13);
			}
			.highlight-yellow {
				color: rgb(223, 171, 1);
			}
			.highlight-teal {
				color: rgb(15, 123, 108);
			}
			.highlight-blue {
				color: rgb(11, 110, 153);
			}
			.highlight-purple {
				color: rgb(105, 64, 165);
			}
			.highlight-pink {
				color: rgb(173, 26, 114);
			}
			.highlight-red {
				color: rgb(224, 62, 62);
			}
			.highlight-gray_background {
				background: rgb(235, 236, 237);
			}
			.highlight-brown_background {
				background: rgb(233, 229, 227);
			}
			.highlight-orange_background {
				background: rgb(250, 235, 221);
			}
			.highlight-yellow_background {
				background: rgb(251, 243, 219);
			}
			.highlight-teal_background {
				background: rgb(221, 237, 234);
			}
			.highlight-blue_background {
				background: rgb(221, 235, 241);
			}
			.highlight-purple_background {
				background: rgb(234, 228, 242);
			}
			.highlight-pink_background {
				background: rgb(244, 223, 235);
			}
			.highlight-red_background {
				background: rgb(251, 228, 228);
			}
			.block-color-default {
				color: inherit;
				fill: inherit;
			}
			.block-color-gray {
				color: rgba(55, 53, 47, 0.6);
				fill: rgba(55, 53, 47, 0.6);
			}
			.block-color-brown {
				color: rgb(100, 71, 58);
				fill: rgb(100, 71, 58);
			}
			.block-color-orange {
				color: rgb(217, 115, 13);
				fill: rgb(217, 115, 13);
			}
			.block-color-yellow {
				color: rgb(223, 171, 1);
				fill: rgb(223, 171, 1);
			}
			.block-color-teal {
				color: rgb(15, 123, 108);
				fill: rgb(15, 123, 108);
			}
			.block-color-blue {
				color: rgb(11, 110, 153);
				fill: rgb(11, 110, 153);
			}
			.block-color-purple {
				color: rgb(105, 64, 165);
				fill: rgb(105, 64, 165);
			}
			.block-color-pink {
				color: rgb(173, 26, 114);
				fill: rgb(173, 26, 114);
			}
			.block-color-red {
				color: rgb(224, 62, 62);
				fill: rgb(224, 62, 62);
			}
			.block-color-gray_background {
				background: rgb(235, 236, 237);
			}
			.block-color-brown_background {
				background: rgb(233, 229, 227);
			}
			.block-color-orange_background {
				background: rgb(250, 235, 221);
			}
			.block-color-yellow_background {
				background: rgb(251, 243, 219);
			}
			.block-color-teal_background {
				background: rgb(221, 237, 234);
			}
			.block-color-blue_background {
				background: rgb(221, 235, 241);
			}
			.block-color-purple_background {
				background: rgb(234, 228, 242);
			}
			.block-color-pink_background {
				background: rgb(244, 223, 235);
			}
			.block-color-red_background {
				background: rgb(251, 228, 228);
			}
			.select-value-color-default {
				background-color: rgba(206, 205, 202, 0.5);
			}
			.select-value-color-gray {
				background-color: rgba(155, 154, 151, 0.4);
			}
			.select-value-color-brown {
				background-color: rgba(140, 46, 0, 0.2);
			}
			.select-value-color-orange {
				background-color: rgba(245, 93, 0, 0.2);
			}
			.select-value-color-yellow {
				background-color: rgba(233, 168, 0, 0.2);
			}
			.select-value-color-green {
				background-color: rgba(0, 135, 107, 0.2);
			}
			.select-value-color-blue {
				background-color: rgba(0, 120, 223, 0.2);
			}
			.select-value-color-purple {
				background-color: rgba(103, 36, 222, 0.2);
			}
			.select-value-color-pink {
				background-color: rgba(221, 0, 129, 0.2);
			}
			.select-value-color-red {
				background-color: rgba(255, 0, 26, 0.2);
			}

			.checkbox {
				display: inline-flex;
				vertical-align: text-bottom;
				width: 16;
				height: 16;
				background-size: 16px;
				margin-left: 2px;
				margin-right: 5px;
			}

			.checkbox-on {
				background-image: url('data:image/svg+xml;charset=UTF-8,%3Csvg%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%0A%3Crect%20width%3D%2216%22%20height%3D%2216%22%20fill%3D%22%2358A9D7%22%2F%3E%0A%3Cpath%20d%3D%22M6.71429%2012.2852L14%204.9995L12.7143%203.71436L6.71429%209.71378L3.28571%206.2831L2%207.57092L6.71429%2012.2852Z%22%20fill%3D%22white%22%2F%3E%0A%3C%2Fsvg%3E');
			}

			.checkbox-off {
				background-image: url('data:image/svg+xml;charset=UTF-8,%3Csvg%20width%3D%2216%22%20height%3D%2216%22%20viewBox%3D%220%200%2016%2016%22%20fill%3D%22none%22%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%3E%0A%3Crect%20x%3D%220.75%22%20y%3D%220.75%22%20width%3D%2214.5%22%20height%3D%2214.5%22%20fill%3D%22white%22%20stroke%3D%22%2336352F%22%20stroke-width%3D%221.5%22%2F%3E%0A%3C%2Fsvg%3E');
			}
		</style>
	</head>
	<body>
		<article id="002feeef-38f3-4ede-9f25-4893f6581cfd" class="page sans">
			<header>
				<h1 class="page-title">Predator and Prey simulator</h1>
				<table class="properties">
					<tbody>
						<tr class="property-row property-row-created_time">
							<th>
								<span class="icon property-icon"
									><svg
										viewBox="0 0 14 14"
										style="width: 14px; height: 14px; display: block; fill: rgba(55, 53, 47, 0.4); flex-shrink: 0; -webkit-backface-visibility: hidden"
										class="typesCreatedAt"
									>
										<path
											d="M6.98643729,14.0000972 C5.19579566,14.0000972 3.40419152,13.3106896 2.04245843,11.9323606 C-0.681017475,9.21200555 -0.680780251,4.76029539 2.04293482,2.04012507 C4.76664406,-0.68004331 9.22427509,-0.68004331 11.9480135,2.04013479 C13.272481,3.36277455 14,5.1330091 14,6.99552762 C14,8.87640182 13.2721894,10.6285043 11.9480135,11.9509302 C10.5679344,13.3105924 8.77756503,14.0000972 6.98643729,14.0000972 Z M10.2705296,7.00913883 L10.2705296,8.46099754 L10.2705296,8.65543362 L10.076181,8.65543362 L8.6543739,8.65543362 L5.72059514,8.65543362 L5.52619796,8.65543362 L5.52619796,8.46099754 L5.52619796,5.52541044 L5.52619796,3.37946773 L5.52619796,3.18502193 L5.72059514,3.18502193 L7.17253164,3.18502193 L7.36692883,3.18502193 L7.36692883,3.37946773 L7.36692883,6.81467358 L10.076181,6.81467358 L10.2705296,6.81467358 L10.2705296,7.00913883 Z M12.1601539,6.99552762 C12.1601539,5.61697497 11.6190112,4.32597154 10.6393933,3.34769528 C8.63253764,1.34336744 5.35197452,1.34061603 3.34153136,3.33944106 C3.33868273,3.34219247 3.33607716,3.34494388 3.33322852,3.34769528 C1.32397148,5.35459953 1.32372842,8.63641682 3.33322852,10.6433794 C5.34295224,12.6504489 8.62968901,12.6504489 10.6393933,10.6433794 C11.6190112,9.66506426 12.1601539,8.37408027 12.1601539,6.99552762 Z"
										></path></svg></span
								>Created
							</th>
							<td><time>@October 10, 2021 12:55 PM</time></td>
						</tr>
						<tr class="property-row property-row-checkbox">
							<th>
								<span class="icon property-icon"
									><svg
										viewBox="0 0 14 14"
										style="width: 14px; height: 14px; display: block; fill: rgba(55, 53, 47, 0.4); flex-shrink: 0; -webkit-backface-visibility: hidden"
										class="typesCheckbox"
									>
										<path
											d="M0,3 C0,1.34314 1.34326,0 3,0 L11,0 C12.6567,0 14,1.34314 14,3 L14,11 C14,12.6569 12.6567,14 11,14 L3,14 C1.34326,14 0,12.6569 0,11 L0,3 Z M3,1.5 C2.17139,1.5 1.5,2.17157 1.5,3 L1.5,11 C1.5,11.8284 2.17139,12.5 3,12.5 L11,12.5 C11.8286,12.5 12.5,11.8284 12.5,11 L12.5,3 C12.5,2.17157 11.8286,1.5 11,1.5 L3,1.5 Z M2.83252,6.8161 L3.39893,6.27399 L3.57617,6.10425 L3.92334,5.77216 L4.26904,6.10559 L4.44531,6.27582 L5.58398,7.37402 L9.28271,3.81073 L9.45996,3.64008 L9.80664,3.3056 L10.1538,3.63989 L10.3311,3.81067 L10.8936,4.35303 L11.0708,4.52399 L11.4434,4.88379 L11.0708,5.24353 L10.8936,5.41437 L6.1084,10.0291 L5.93115,10.2 L5.58398,10.5344 L5.23682,10.2 L5.05957,10.0292 L2.83057,7.87946 L2.65283,7.70801 L2.27832,7.34674 L2.6543,6.98694 L2.83252,6.8161 Z"
										></path></svg></span
								>Pin
							</th>
							<td><div class="checkbox checkbox-off"></div></td>
						</tr>
						<tr class="property-row property-row-url">
							<th>
								<span class="icon property-icon"
									><svg
										viewBox="0 0 14 14"
										style="width: 14px; height: 14px; display: block; fill: rgba(55, 53, 47, 0.4); flex-shrink: 0; -webkit-backface-visibility: hidden"
										class="typesUrl"
									>
										<path
											d="M3.73333,3.86667 L7.46667,3.86667 C8.49613,3.86667 9.33333,4.70387 9.33333,5.73333 C9.33333,6.7628 8.49613,7.6 7.46667,7.6 L6.53333,7.6 C6.01813,7.6 5.6,8.0186 5.6,8.53333 C5.6,9.04807 6.01813,9.46667 6.53333,9.46667 L7.46667,9.46667 C9.5284,9.46667 11.2,7.79507 11.2,5.73333 C11.2,3.6716 9.5284,2 7.46667,2 L3.73333,2 C1.6716,2 0,3.6716 0,5.73333 C0,7.124 0.762067,8.33453 1.88953,8.97713 C1.87553,8.83107 1.86667,8.6836 1.86667,8.53333 C1.86667,7.92013 1.98753,7.33447 2.2036,6.7978 C1.99267,6.4954 1.86667,6.12953 1.86667,5.73333 C1.86667,4.70387 2.70387,3.86667 3.73333,3.86667 Z M12.1095,5.28907 C12.1231,5.4356 12.1333,5.58307 12.1333,5.73333 C12.1333,6.34607 12.0101,6.9294 11.7931,7.46513 C12.0059,7.768 12.1333,8.13573 12.1333,8.53333 C12.1333,9.5628 11.2961,10.4 10.2667,10.4 L6.53333,10.4 C5.50387,10.4 4.66667,9.5628 4.66667,8.53333 C4.66667,7.50387 5.50387,6.66667 6.53333,6.66667 L7.46667,6.66667 C7.98187,6.66667 8.4,6.24807 8.4,5.73333 C8.4,5.2186 7.98187,4.8 7.46667,4.8 L6.53333,4.8 C4.4716,4.8 2.8,6.4716 2.8,8.53333 C2.8,10.59507 4.4716,12.2667 6.53333,12.2667 L10.2667,12.2667 C12.3284,12.2667 14,10.59507 14,8.53333 C14,7.14267 13.2375,5.93167 12.1095,5.28907 Z"
										></path></svg></span
								>Repository
							</th>
							<td></td>
						</tr>
					</tbody>
				</table>
			</header>
			<div class="page-body">
				<h2 id="49e99981-83ed-434c-a87b-4b4f17b01144" class="">A website simulating the relations between predator and prey</h2>
				<p id="83db2842-11a6-4ddb-b7fa-ba6461244b20" class=""></p>
				<p id="6ce8e16d-67e1-45d0-8c83-d8972ad347ff" class="">
					Within the topic ecology in my biology class our teacher had prepared a game for one of the lessons. We were given a sheet of rules and about 200 matches. The game was supposed to
					simulate the relations between the population of prey and the population of predators. But really? Using matches? It would take hours to even get a feeling whether the algorithm
					our teacher gave us was any good (Spoiler, the algorithm is flawed). So i decided to write a program and visualize the graph on a website.
				</p>
				<p id="64de29a1-115b-4cf2-9c37-6e102eed9005" class=""></p>
				<h2 id="5c01db26-b258-4d47-97bc-a0f9f6b8834a" class="">The algorithm</h2>
				<p id="85f511a6-3a9c-4927-a97a-2a67e06877af" class="">
					Two pairs are picked. If the pair contains two prey, there is a 50% chance they will breed. If the pair consists of 2 predators, they both die. If the pair consists of a prey and a
					predator, there is a 50% chance the predator kills they prey and gets a child, if the prey escapes they both survive.
				</p>
				<p id="66bbb80a-70b4-484d-8833-c101b6982e80" class=""></p>
				<h2 id="aedfabf3-1c15-4c5e-a210-95a1470c43fb" class="">The features</h2>
				<ul id="3c3f7689-5211-4e52-b801-86464ab9ba59" class="bulleted-list">
					<li style="list-style-type: disc">Simulating the population of predator and prey in relation with one another</li>
				</ul>
				<ul id="86e36005-fb41-4a3b-bb39-3242c6640638" class="bulleted-list">
					<li style="list-style-type: disc">Visualizing the values in a graph</li>
				</ul>
				<h2 id="dcbe8f21-c5e5-4a34-aef2-6b30b93add11" class="">The challenges</h2>
				<ul id="3ed3c727-752b-4117-853f-3815d7ccfcd5" class="bulleted-list">
					<li style="list-style-type: disc">
						At first i randomly chose predator and prey with a 50% chance, therfore there often was an uneven amount of predators and prey. I fixed this by creating two arrays of length
						500, one for predators and one for prey and then randomly picking and removing an item from the array.
					</li>
				</ul>
				<ul id="6f70ca02-f33b-42af-95d7-629d6bfdf008" class="bulleted-list">
					<li style="list-style-type: disc">
						Finding a the right starting population. The amount our teacher gave us was 20, but since the algorithm is flawed both populations were 0 after about 10-20 rounds.
					</li>
				</ul>
				<p id="2551d9e0-afa2-4c7b-87a3-3725e303e761" class=""></p>
				<h2 id="a15d8bbf-0619-45ee-9e2f-9c0ba8eac998" class="">The critics</h2>
				<ul id="47e546cb-9a05-4ca4-b900-457455dc4899" class="bulleted-list">
					<li style="list-style-type: disc">
						The algorithm is flawed. The population should vary periodically which means that the average population should stay the same over time. In this case however the average
						population varies extremly. I.e it goes from an average of 350 prey to an average of 50 and then escalates to a 1000 average. Something the algorithm is able to do fairly well,
						is showing that the change in population is delayed in relation to the population of prey.
					</li>
				</ul>
				<p id="6d72c8ef-1277-47a3-80d6-fb33a10596fc" class=""></p>
				<p id="e2f36bf5-d438-4b90-947e-b2e72882b024" class=""></p>
			</div>
		</article>
	</body>
</html>
