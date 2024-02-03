<script>
	import { onMount } from 'svelte';

	const stations = [
		'Tha Phra',
		'Charan 13',
		'Fai Chai',
		'Bang Khun Non',
		'Bang Yi Khan',
		'Sirindhorn',
		'Bang Phlat',
		'Bang O',
		'Bang Pho',
		'Tao Poon',
		'Bang Sue',
		'Kamphaeng Phet',
		'Chatuchak Park',
		'Phahon Yothin',
		'Lat Phrao',
		'Ratchadaphisek',
		'Sutthisan',
		'Huai Khwang',
		'Thailand Cultural Centre',
		'Phra Ram 9',
		'Phetchaburi',
		'Sukhumvit',
		'Queen Sirikit National Convention Centre',
		'Khlong Toei',
		'Lumphini',
		'Si Lom',
		'Sam Yan',
		'Hua Lamphong',
		'Wat Mangkon',
		'Sam Yot',
		'Sanam Chai',
		'Itsaraphap',
		'Tha Phra',
		'Bang Phai',
		'Bang Wa',
		'Phetkasem 48',
		'Phasi Charoen',
		'Bang Khae',
		'Lak Song'
	];
	const thaiStationName = [
		'ท่าพระ',
		'จรัญฯ 13',
		'ไฟฉาย',
		'บางขุนนนท์',
		'บางยี่ขัน',
		'สิรินธร',
		'บางพลัด',
		'บางอ้อ',
		'บางโพ',
		'เตาปูน',
		'บางซื่อ',
		'กำแพงเพชร',
		'สวนจตุจักร',
		'พหลโยธิน',
		'ลาดพร้าว',
		'รัชดาภิเษก',
		'สุทธิสาร',
		'ห้วยขวาง',
		'ศูนย์วัฒนธรรมแห่งประเทศไทย',
		'พระราม 9',
		'เพชรบุรี',
		'สุขุมวิท',
		'ศูนย์การประชุมแห่งชาติสิริกิติ์',
		'คลองเตย',
		'ลุมพินี',
		'สีลม',
		'สามย่าน',
		'หัวลำโพง',
		'วัดมังกร',
		'สามยอด',
		'สนามชัย',
		'อิสรภาพ',
		'ท่าพระ',
		'บางไผ่',
		'บางหว้า',
		'เพชรเกษม 48',
		'ภาษีเจริญ',
		'บางแค',
		'หลักสอง'
	];

	/**
	 * @type {string | null}
	 */
	let selectedStation = stations[0];
	/**
	 * @type {string | null}
	 */
	let thaiSelectedStation = thaiStationName[0];
	let State = 1;
	let THTerminalStation = '';
	let ENTerminalStation = '';
	async function fetchData() {
		const response = await fetch('/api/add');
		if (response.ok) {
			const json = await response.json();
			const stationIndex = json.body.Station; // Assuming this is a zero-based index
			const TerminalStation = json.body.TerminalStation;
			if (stationIndex >= 0 && stationIndex < stations.length) {
				selectedStation = stations[stationIndex];
				thaiSelectedStation = thaiStationName[stationIndex];
				ENTerminalStation = stations[TerminalStation];
				THTerminalStation = thaiStationName[TerminalStation];
			}
			const DisplayState = json.body.DisplayState;
			State = DisplayState;
		}
	}

	onMount(() => {
		let interval = setInterval(fetchData, 1000); // Poll every 5 seconds
		console;
		return () => {
			clearInterval(interval);
		};
	});
</script>

		{#if selectedStation !== null && State == 2}
		<head>
			<meta charset="UTF-8">
			<meta name="viewport" content="width=device-width, initial-scale=1.0">
			<meta http-equiv="X-UA-Compatible" content="ie=edge">
			<meta name="DRM" content="DRM">
			<title>DRM</title>
			<!--<meta http-equiv="refresh" content="15;url=DRMRNB01.html" />-->
			<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css">
			<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js"></script>
			<link href="https://fonts.googleapis.com/css?family=Niramit:400,700&display=swap" rel="stylesheet">
			<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.5/jquery.min.js"></script>
			<script src="bodyswapscript.js"></script>
		  <link rel="stylesheet" href="stylesRN01.css">
		  <link rel="stylesheet" href="animate.css">
		  <link rel="icon" href="RAILWAYLOGO2019.png">
			  <script src="wow.min.js"></script>
			  <script src="clockEN.js"></script>
			  <script src="KeyboardEvent.js"></script>
			  <body onload="startTime()">
		</head>
		<body id="test">
			<ul class="animated fadeInDown">
				<li1><img class="animated fadeInDown delay-1s" src="RAILWAYLOGO2019.png"><h1 class="animated fadeInDown delay-1s">สายสีเเดงเข้ม</h1> 
				  <h2 class="animated fadeInDown delay-1s">DarkRed Line</h2></li1>
				<li2 class=" animated  fadeInDown delay-0.75s">
					<h3  class=" animated fadeInDown delay-1s">สถานีต่อไป | Next Station</h3> 
					<li0> <div class="ripple animated fadeInUp delay-1s">RN02</div> </li0>
				  <h1 class="animated fadeInUp delay-1s">{thaiSelectedStation}</h1>
				  <h2 class="animated  fadeInUp delay-1s">{selectedStation}</h2>
				 </li2>
				<li3 class=" animated zoomIn delay-0.75s">
					<h1 class="animated fadeInDown delay-1s">ประตูเปิดด้านนี้</h1>
					<h2 class="animated fadeInDown delay-1s">Door open this side.</h2>
					<h3 class="animated pulse delay-1s">▮▮</h3>
				</li3>
				<li4 class=" animated fadeInDown delay-0.75s">
				  <h1 class="animated fadeInDown delay-1s">ปลายทาง | Destination</h1>
				  <li1> <div class="rippleter animated fadeInUp delay-1s">RN10</div> </li1>
				  <h2 class="animated  fadeInUp delay-1s">{THTerminalStation}</h2>
				  <h3 class="animated  fadeInUp delay-1s">{ENTerminalStation}</h3>
				  </li4>
			  </ul>
			<div class="bar animated fadeIn">
				<div></div>
			  </div>
			  <div class="bar2 animated fadeIn">
				  <div></div>
				</div>
				<div class="bar3 animated fadeIn">
					<div></div>
				  </div>
				  <div class="blink"></div>
		
			  <div class="ripple1 animated bounceIn">RN01</div>
			  <div class="textt1">จตุจักร
				  <div class="texte1">Chatuchak</div>
			  </div>
		
			  <div class="ripple2">RN02</div>
			  <div class="textt2">{thaiSelectedStation}
				  <div class="texte2">{selectedStation}</div>
			  </div>
		
			  <div class="ripple3 animated bounceIn delay-1s">RN03</div>
			  <div class="textt3 animated fadeIn delay-1s">วัดเสมียนนารี
				  <div class="texte3 animated fadeIn delay-1s">Wat Samian Nari</div>
			  </div>
		
			  <div class="ripple4 animated bounceIn delay-1s">RN04</div>
			  <div class="textt4 animated fadeIn delay-1s">บางเขน
				  <div class="texte4 animated fadeIn delay-1s">Bang Khen</div>
			  </div>
		
			  <div class="ripple5 animated bounceIn delay-1s">RN05</div>
			  <div class="textt5 animated fadeIn delay-1s">ทุ่งสองห้อง
				  <div class="texte5 animated fadeIn delay-1s">Thung Song Hong</div>
			  </div>
		
			  <div class="triangle-right animated heartBeat"></div>
		</body>
		<footer class="animated fadeInUp"> 
			<lif1>
		 <h1 class="animated fadeInUp delay-1s" id="txt"></h1> 
		</lif1>
		 <lif2>
		 <h1 class="animated fadeInUp delay-1s">ตู้ที่ | Car No.</h1> 
		 </lif2>  
		 <lif3>
		 <h1 class="ripplecar animated fadeInUp delay-1s">1</h1>
		 </lif3>  
		  </footer>

		
		{:else if selectedStation !== null && State == 1}
		<head>
			<meta charset="UTF-8">
			<meta name="viewport" content="width=device-width, initial-scale=1.0">
			<meta http-equiv="X-UA-Compatible" content="ie=edge">
			<meta name="DRM" content="DRM">
			<title>DRM</title>
			<!--<meta http-equiv="refresh" content="15;url=DRMRNB01.html" />-->
			<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css">
			<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js"></script>
			<link href="https://fonts.googleapis.com/css?family=Niramit:400,700&display=swap" rel="stylesheet">
			<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.5/jquery.min.js"></script>
			<script src="bodyswapscript.js"></script>
		  <link rel="stylesheet" href="stylesStationRN01.css">
		  <link rel="stylesheet" href="animate.css">
		  <link rel="icon" href="RAILWAYLOGO2019.png">
			  <script src="wow.min.js"></script>
			  <script src="clockEN.js"></script>
			  <script src="KeyboardEvent.js"></script>
			  <body onload="startTime()">
		</head>
		
		<body id="test">
			<ul class="wow animated fadeInDown" data-wow-delay="0.2s">
				<li1><img class="animated fadeInLeft delay-1s" src="RAILWAYLOGO2019.png"><h1 class="animated fadeInDown delay-1s">สายสีเเดงเข้ม</h1> 
				  <h2 class="animated fadeInDown delay-1s">DarkRed Line</h2></li1>
				<li2 class=" animated fadeInDown delay-0.75s">
					<h3 class=" animated fadeInDown delay-1s">เชื่อมต่อกับ | Connecting With</h3> 
					<li0> <img class="animated fadeInDown delay-1s" src="LRLineLA.png">
						<img class="animated fadeInDown delay-1s" src="BLLineLA.png"></li0>
				 </li2>
				<li3 class=" animated zoomIn delay-0.75s">
					<h1 class="animated fadeInDown delay-1s">ประตูเปิดด้านนี้</h1>
					<h2 class="animated fadeInDown delay-1s">Door open this side.</h2>
					<h3 class="animated pulse delay-1s">▮▮</h3>
				</li3>
				<li4 class="animated fadeInDown delay-0.75s">
				  <h1 class="animated fadeInDown delay-1s"> ปลายทาง | Destination</h1>
				  <li1> <div class="rippleter animated fadeInDown  delay-1s">RN10</div> </li1>
				  <h2 class="animated fadeInDown delay-1s">รังสิต</h2>
				  <h3 class="animated fadeInDown delay-1s">Rangsit</h3>
				  </li4>
			  </ul>
		   
		
			  <div class="animated fadeInLeft delay-1s textt3" >ขณะนี้กำลังจอดที่
				  <div class="animated fadeInleft delay-1s texte3">Now stopping at</div>
			  </div>
		
			  <div class="ripple2">RN01</div>
			  <div class="textt2 animated zoomInUp delay-1s">{thaiSelectedStation}
			<div class="texte2 animated zoomInUp delay-1s">{selectedStation}</div>
			  </div>
		
		</body >
		<footer class="animated fadeInUp"> 
			<lif1>
		 <h1 class="animated fadeInUp delay-1s" id="txt"></h1> 
		</lif1>
		 <lif2>
		 <h1 class="animated fadeInUp delay-1s">ตู้ที่ | Car No.</h1> 
		 </lif2>  
		 <lif3>
		 <h1 class="ripplecar animated fadeInUp delay-1s">1</h1>
		 </lif3>  
		  </footer>

		{:else if selectedStation !== null && State == 0}

			<head>
				<meta charset="UTF-8">
				<meta name="viewport" content="width=device-width, initial-scale=1.0">
				<meta http-equiv="X-UA-Compatible" content="ie=edge">
				<meta name="DRM" content="DRM">
				<title>DRM</title>
				<!--<meta http-equiv="refresh" content="15;url=DRMRNB01.html" />-->
				<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css">
				<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js"></script>
				<link href="https://fonts.googleapis.com/css?family=Niramit:400,700&display=swap" rel="stylesheet">
				<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.5/jquery.min.js"></script>
				<script src="bodyswapscript.js"></script>
			  <link rel="stylesheet" href="stylesStationRN01.css">
			  <link rel="stylesheet" href="animate.css">
			  <link rel="icon" href="RAILWAYLOGO2019.png">
				  <script src="wow.min.js"></script>
				  <script src="clockEN.js"></script>
				  <script src="KeyboardEvent.js"></script>
				  <body onload="startTime()">
			</head>
		<body id="test">
			<ul class="wow animated fadeInDown" data-wow-delay="0.2s">
				<li1><img class="animated fadeInLeft delay-1s" src="RAILWAYLOGO2019.png"><h1 class="animated fadeInDown delay-1s">สายสีเเดงเข้ม</h1> 
				  <h2 class="animated fadeInDown delay-1s">DarkRed Line</h2></li1>
				<li2 class=" animated fadeInDown delay-0.75s">
					<h3 class=" animated fadeInDown delay-1s">เชื่อมต่อกับ | Connecting With</h3> 
					<li0> <img class="animated fadeInDown delay-1s" src="LRLineLA.png">
						<img class="animated fadeInDown delay-1s" src="BLLineLA.png"></li0>
				 </li2>
				<li3 class=" animated zoomIn delay-0.75s">
					<h1 class="animated fadeInDown delay-1s">ประตูเปิดด้านนี้</h1>
					<h2 class="animated fadeInDown delay-1s">Door open this side.</h2>
					<h3 class="animated pulse delay-1s">▮▮</h3>
				</li3>
				<li4 class="animated fadeInDown delay-0.75s">
				  <h1 class="animated fadeInDown delay-1s"> ปลายทาง | Destination</h1>
				  <li1> <div class="rippleter animated fadeInDown  delay-1s">RN10</div> </li1>
				  <h2 class="animated fadeInDown delay-1s">{THTerminalStation}</h2>
				  <h3 class="animated fadeInDown delay-1s">{ENTerminalStation}</h3>
				  </li4>
			  </ul>
		   
		
			  <div class="animated fadeInLeft delay-1s textt3" >ขณะนี้กำลังจอดที่
				  <div class="animated fadeInleft delay-1s texte3">Now stopping at</div>
			  </div>
		
			  <div class="ripple2">RN01</div>
			  <div class="textt2 animated zoomInUp delay-1s">{thaiSelectedStation}
			<div class="texte2 animated zoomInUp delay-1s">{selectedStation}</div>
			  </div>
		
		</body >
		<footer class="animated fadeInUp"> 
			<lif1>
		 <h1 class="animated fadeInUp delay-1s" id="txt"> </h1> 
		 
		</lif1>
		<lif1>
			<h2 class="animated fadeInUp delay-1s">รถไฟสิ้นสุดให้บริการที่สถานีนี้</h2> <h3 class="animated fadeInUp delay-1s">This train terminate here</h3> 
		   </lif1>
		   
		 <lif2>
		 <h1 class="animated fadeInUp delay-1s">ตู้ที่ | Car No.</h1> 
		 </lif2>  
		 <lif3>
		 <h1 class="ripplecar animated fadeInUp delay-1s">1</h1>
		 </lif3>  
		  </footer>

		{:else if State == 3}
			<div class="my-auto text-center absolute flex w-full">
				<div class="mx-auto lg:mt-80 justify-items-center content-center">
					<p class=" text-4xl lg:text-9xl text-white text-bold mb-10">
						ผู้โดยสารโปรดทราบ / Attention Please
					</p>
					<p class=" text-3xl lg:text-5xl text-white">
						เนื่องจากมีเหตุขัดข้องในระบบเดินรถทำให้ขบวนไม่สามารถเคลื่อนที่ได้
						ขณะนี้กำลังอยู่ระหว่างการดำเนินแก้ไขกรุณารอสักครู่
					</p>
					<p class="text-3xl lg:text-5xl text-white mb-4">ขออภัยในความไม่สะดวก</p>
					<p class="text-3xl lg:text-5xl text-white">
						Due to technical problem, This train will be delayed. We apologise for any
						inconvenience.
					</p>
				</div>
				<audio controls autoplay hidden  src="/arriving.wav">
				  </audio>
			</div>
		{:else}
			<div>Loading station data...</div>
			<audio controls   src="/arriving.wav"></audio>
		{/if}

