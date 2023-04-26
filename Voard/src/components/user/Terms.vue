<template>
  <v-app>
    <v-app-bar>
      <v-app-bar-title>약관</v-app-bar-title>
    </v-app-bar>
    <v-main>
      <v-container>
        <v-sheet max-width="800" class="mx-auto mt-16">
          <v-textarea
            label="이용약관"
            variant="outlined"
            rows="10"
            hide-details="true"
            v-model="data.terms"
          ></v-textarea>
          <v-checkbox
            class="d-flex justify-end"
            label="동의합니다."
            v-model="data.isCheck1"
          ></v-checkbox>
          <v-textarea
            label="개인정보 취급방침"
            variant="outlined"
            rows="10"
            hide-details="true"
            v-model="data.privacy"
          ></v-textarea>
          <v-checkbox
            class="d-flex justify-end"
            label="동의합니다."
            v-model="data.isCheck2"
          ></v-checkbox>
        </v-sheet>
        <v-sheet max-width="800" class="mx-auto text-center">
          <v-btn @click="btnCancel">취소</v-btn>
          <v-btn class="ml-2" color="primary" @click="btnNext">다음</v-btn>
        </v-sheet>
      </v-container>
    </v-main>
    <v-footer app theme="dark">copyright &copy;Voard v1.0</v-footer>
  </v-app>
</template>
<script setup>
import axios from "axios";
import { useRouter } from "vue-router";
import { reactive } from "vue";
import { onBeforeMount } from "vue";

const router = useRouter();

const data = reactive({
  terms: null,
  privacy: null,
  isCheck1: false,
  isCheck2: false,
});

const btnCancel = () => {
  router.push("/user/login");
};
const btnNext = () => {
  if (data.isCheck1 && data.isCheck2) {
    router.push("/user/register");
  } else {
    alert("동의체크를 하셔야  합니다.");
  }
};

onBeforeMount(() => {
  axios
    .get("http://localhost:8080/Voard/user/terms")
    .then((response) => {
      console.log(response);
      data.terms = response.data.terms;
      data.privacy = response.data.privacy;
      data.isCheck1 = response.data.isCheck1;
      data.isCheck2 = response.data.isCheck2;
    })
    .catch((error) => {
      console.log(error);
    });
});
</script>
<style scoped></style>
