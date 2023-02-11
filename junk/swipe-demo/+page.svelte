<script>
	import { Swiper, SwiperSlide } from 'swiper/svelte';

	// Import Swiper styles
	import 'swiper/css';

	import 'swiper/css/effect-coverflow';
	import 'swiper/css/pagination';

	// global styles zijn hierin nodig >>> dus styles.css
	import '$lib/swipe-styles.css';

	// import required modules
	import { EffectCoverflow, Pagination } from 'swiper';
</script>

<Swiper
	effect={'coverflow'}
	grabCursor={true}
	centeredSlides={true}
	slidesPerView={'auto'}
	coverflowEffect={{
		rotate: 50,
		stretch: 0,
		depth: 500,
		modifier: 1,
		slideShadows: true
	}}
	pagination={true}
	modules={[EffectCoverflow, Pagination]}
	class="mySwiper"
>
	<a href="https://www.youtube.com/watch?v=JrEh8cpabII"
		><SwiperSlide><img src="https://swiperjs.com/demos/images/nature-1.jpg" /></SwiperSlide>
	</a>
	<SwiperSlide><img src="https://swiperjs.com/demos/images/nature-2.jpg" /></SwiperSlide
	><SwiperSlide><img src="https://swiperjs.com/demos/images/nature-3.jpg" /></SwiperSlide
	><SwiperSlide><img src="https://swiperjs.com/demos/images/nature-4.jpg" /></SwiperSlide
	><SwiperSlide><img src="https://swiperjs.com/demos/images/nature-5.jpg" /></SwiperSlide
	><SwiperSlide><img src="https://swiperjs.com/demos/images/nature-6.jpg" /></SwiperSlide
	><SwiperSlide><img src="https://swiperjs.com/demos/images/nature-7.jpg" /></SwiperSlide
	><SwiperSlide><img src="https://swiperjs.com/demos/images/nature-8.jpg" /></SwiperSlide
	><SwiperSlide><img src="https://swiperjs.com/demos/images/nature-9.jpg" /></SwiperSlide>
</Swiper>
