<template>
	<div>
		<div id="modifiers">
			<div @click="clickDiv">
				<!--			<div @click.capture="clickDiv">-->
				DIV 영역
				<p @click.self="clickP">
					<!--				<p @click.capture="clickP">-->
					P 영역
					<!--					<span @click="clickSpan">SPAN 영역</span>-->
					<span @click="clickSpan">SPAN 영역</span>
					<a href="https://naver.com" @click.prevent.stop="clickA">a 영역</a>
				</p>
			</div>
		</div>
		<!--		<a href="https://naver.com" @click.prevent="clickA">a 영역</a>-->
	</div>
</template>

<script>
export default {
	setup() {
		const clickDiv = () => {
			console.log('clickDiv');
			// location.href = 'https://naver.com';
		};
		const clickP = () => {
			console.log('clickP');
		};
		const clickSpan = e => {
			console.log('clickSpan');
			// e.stopPropagation(); // 이벤트 전파 막기
			// alert('좋아요');
		};
		const clickA = e => {
			e.preventDefault();
			alert('어떤 기능~');
		};

		return { clickDiv, clickP, clickSpan, clickA };
	},
};
</script>

<style lang="css" scoped>
#modifiers div,
#modifiers p,
#modifiers span {
	padding: 40px;
}
#modifiers div {
	background-color: #ccc;
}
#modifiers p {
	background-color: #999;
}
#modifiers span {
	background-color: #666;
	display: block;
}
</style>
