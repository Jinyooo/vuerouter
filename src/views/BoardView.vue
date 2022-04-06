<template>
    <div class="board">
    <h3>게시글 목록입니다</h3>

    <a v-for="n in 10" :key="n">
        <router-link :to=" `/board/${n}` ">{{ n }}</router-link> |
    </a>

    <!-- 위에 작성한 router-link의 컴포넌트가 출력되는 곳 -->
    <router-view></router-view>
    </div>
</template>

<script>

export default {
    name: 'BoardView',
    data :()=> ({
        num: 10
    })

}
</script>