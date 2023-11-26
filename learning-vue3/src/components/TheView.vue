<template>
	<main>
		<div class="container py-4">
			<PostCreate @create-post="createPost"></PostCreate>

			<hr class="my-4" />

			<div class="row g-3">
				<div v-for="post in posts" :key="post.id" class="col-4">
					<AppCard
						:title="post.title"
						:contents="post.contents"
						:type="post.type"
						:is-like="post.isLike"
						@toggle-like="post.isLike = !post.isLike"
					></AppCard>
				</div>
			</div>

			<hr class="my-4" />
			<!--
              modelValue
              update:modelValue
            -->
			<!--				<input v-model="username" type="text" />-->
			<!--      :model-value="username"-->
			<!--      @update:modelValue="value => (username = value)"-->
			<LabelInput v-model="username" label="이름"> </LabelInput>
			<LabelTitle v-model:title="username" label="제목"> </LabelTitle>
			<UserName
				v-model:firstName="firstName"
				v-model:lastName="lastName"
			></UserName>
		</div>
	</main>
</template>

<script>
import AppCard from '@/components/AppCard.vue';
import PostCreate from '@/components/PostCreate.vue';
import LabelInput from '@/components/LabelInput.vue';
import LabelTitle from '@/components/LabelTitle.vue';
import UserName from '@/components/UserName.vue';
import { reactive, ref } from 'vue';
export default {
	components: {
		UserName,
		AppCard,
		PostCreate,
		LabelInput,
		LabelTitle,
	},
	setup() {
		const post = reactive({
			title: '재목2',
			contents: '내용2',
		});
		const posts = reactive([
			{ id: 1, title: '제목1', contents: '내용1', isLike: true, type: 'news' },
			{ id: 2, title: '제목2', contents: '내용2', isLike: true, type: 'news' },
			{ id: 3, title: '제목3', contents: '내용3', isLike: true, type: 'news' },
			{
				id: 4,
				title: '제목4',
				contents: '내용4',
				isLike: false,
				type: 'notice',
			},
			{
				id: 5,
				title: '제목5',
				contents: '내용5',
				isLike: false,
				type: 'notice',
			},
		]);
		const createPost = newPost => {
			console.log('newPost: ', newPost);
			posts.push(newPost);
		};
		const username = ref('');
		const firstName = ref('');
		const lastName = ref('');
		return { post, posts, createPost, username, firstName, lastName };
	},
};
</script>

<style lang="scss" scoped></style>
