<template>
  <v-app>
    <v-app-bar>
      <v-app-bar-title>글쓰기</v-app-bar-title>
      <p>
        OOO님 반갑습니다.
        <v-btn>로그아웃</v-btn>
      </p>
    </v-app-bar>
    <v-main>
      <v-container>
        <v-card>
          <v-form>
            <v-text-field label="제목"></v-text-field>
            <v-textarea label="내용"></v-textarea>
          </v-form>
          <v-card-actions>
            <v-btn color="primary" @click="submit">작성</v-btn>
            <v-btn color="secondary" @click="cancel">취소</v-btn>
          </v-card-actions>
        </v-card>
      </v-container>
    </v-main>
    <v-footer app theme="dark">copyright &copy;Voard v1.0</v-footer>
  </v-app>
</template>
<script setup></script>
<style scoped></style>

<!--<template>
  <v-app>
    <v-app-bar>
      <v-app-bar-title>글쓰기</v-app-bar-title>
      <p>
        {{user.name}}님 반갑습니다.
        <v-btn @click="logout">로그아웃</v-btn>
      </p>
    </v-app-bar>
    <v-main>
      <v-container>
        <v-card>
          <v-form ref="form" v-model="valid">
            <v-text-field
              label="제목"
              v-model="title"
              :rules="[v => !!v || '제목을 입력해주세요']"
            ></v-text-field>
            <v-textarea
              label="내용"
              v-model="content"
              :rules="[v => !!v || '내용을 입력해주세요']"
            ></v-textarea>
          </v-form>
          <v-card-actions>
            <v-btn color="primary" @click="submit">작성</v-btn>
            <v-btn color="secondary" @click="cancel">취소</v-btn>
          </v-card-actions>
        </v-card>
      </v-container>
    </v-main>
    <v-footer app theme="dark">{{footerText}}</v-footer>
  </v-app>
</template>
<script setup>
  import {ref, reactive} from 'vue'
  import {useRouter} from 'vue-router'
  import {getUser, logout} from '../api/auth'

  const user = reactive(getUser())
  const router = useRouter()
  
  const title = ref('')
  const content = ref('')
  const valid = ref(false)

  const submit = () => {
    if (valid.value) {
      // 게시글 작성 API 호출
      console.log(title.value, content.value)

      // 페이지 이동
      router.push('/')
    }
  }

  const cancel = () => {
    router.push('/')
  }

  const logout = () => {
    logout()
    router.replace('/login')
  }

  const footerText = '© Voard v1.0'

</script>
<style scoped></style>

-->
