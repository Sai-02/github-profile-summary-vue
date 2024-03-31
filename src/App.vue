<script setup>
import { ref } from 'vue';
import Loader from './assets/Loader.vue';
import axios from "axios"
import FollowersList from './components/FollowersList.vue';
import ReposList from './components/ReposList.vue';
const loading = ref(false)
const userDetailsRef = ref({})
const followersDataRef = ref({})
const reposDataRef = ref({})
const userNameInputValue = ref("")
const isDataFetched = ref(false)
const handleAnalyze = () => {
  loading.value = true
  handleData()
}

const handleData = async () => {
  try {
    const data = await axios.get("https://api.github.com/users/sai-02")
    userDetailsRef.value = data.data
    const followersData = await axios.get(data.data.followers_url);
    followersDataRef.value = followersData.data
    const reposData = await axios.get(data.data.repos_url)
    reposDataRef.value = reposData
    loading.value = false
    isDataFetched.value = true
  } catch (e) {
    console.log(e)
  }
}
</script>

<template>
  <div class="text-center h-screen w-screen bg-[#eceafb] flex items-center justify-center">
    <div class="bg-white rounded-lg shadow p-4 flex flex-col gap-3" v-show="!loading && !isDataFetched">
      <h3 class="">Enter your github username</h3>
      <input type="text" class="rounded px-2 py-1 border outline-none" v-model="userNameInputValue" />
      <div class="">
        <button class="px-2 py-1 rounded bg-[#7E6EE1] text-white" @click="handleAnalyze">Analyze</button>
      </div>
    </div>
    <div class="" v-show="loading">
      <Loader />
    </div>
    <div class="" v-show="isDataFetched">
      Great data is fetched
      <FollowersList :followersData=followersDataRef />
      <ReposList :reposData=reposDataRef />
    </div>
  </div>
</template>

<style scoped></style>
