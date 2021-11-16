<script setup>
import { ref } from "vue";

const TabItems = ref([
  {icon: 'fas fa-home', title: 'Home', id:'home'},
  {icon: 'fas fa-hashtag', title: 'Explore', id:'explore'},
  {icon: 'fa fa-bell', title: 'Notifications', id:'notifications'},
  {icon: 'fa fa-envelope', title: 'Messages', id:'messages'},
  {icon: 'fa fa-bookmark', title: 'Bookmarks', id:'bookmarks'},
  {icon: 'fa fa-clipboard-list', title: 'Lists', id:'lists'},
  {icon: 'fa fa-user', title: 'Profile', id:'profile'},
  {icon: 'fa fa-ellipsis-h', title: 'More', id:'more'},
]);
const trending = ref([
  {top:'Trending in TX', title:'Gigi', bottom:'Trending with: Rip Gigi'},
  {top:'Music', title:'We Won', bottom:'135k Tweets'},
  {top:'Pop', title:'Blue Ivy', bottom:'40k Tweets'},
  {top:'Trending in US', title:'Denim Day', bottom:'40k Tweets'},
  {top:'Trending', title:'When Beyonce', bottom:'25.4k Tweets'},
]);
const friends = ref([
  {src:'./src/assets/profile-1.png', name:'Drew', handle: '@drew'},
  {src:'./src/assets/profile-2.png', name:'Jagger', handle: '@jagger'},
  {src:'./src/assets/profile-3.png', name:'Owen', handle: '@owen'},
]);
const followers = ref([
  {src:'./src/assets/profile-1.png', name:'Drew',   handler:'@drew',    time:'20 min',  tweet:'Aliquam erat volutpat. Etiam sed suscipit risus. Phasellus porttitor lorem risus, non euismod purus accumsan vel.', comments:'1,000', retweets: '550', likes:'1,250.500'},
  {src:'./src/assets/profile-2.png', name:'Jagger', handler:'@jagger',  time:'55 min',  tweet:'Phasellus porttitor, nunc et ultrices mollis, lacus nulla ultricies urna, id finibus tellus leo quis mi.', comments:'1,000', retweets: '550', likes:'1,250.500'},
  {src:'./src/assets/profile-3.png', name:'Owen',   handler:'@owen',    time:'1.4 hr',  tweet:'Vestibulum ligula ex, commodo quis ante et, tempor commodo lorem.', comments:'1,000', retweets: '550', likes:'1,250.500'},
  {src:'./src/assets/profile-2.png', name:'Jagger', handler:'@jagger',  time:'2 hr',    tweet:'Maecenas sagittis sapien a eleifend luctus. Sed et justo nibh.', comments:'1,000', retweets: '550', likes:'1,250.500'},
  {src:'./src/assets/profile-2.png', name:'Jagger', handler:'@jagger',  time:'2 hr',    tweet:'Maecenas sagittis sapien a eleifend luctus. Sed et justo nibh.', comments:'1,000', retweets: '550', likes:'1,250.500'},
  {src:'./src/assets/profile-1.png', name:'Drew',   handler:'@drew',    time:'5 hr',    tweet:'Pellentesque nibh lorem, bibendum vitae nunc eu, sodales sagittis nisi.', comments:'1,000', retweets: '550', likes:'1,250.500'},
  {src:'./src/assets/profile-1.png', name:'Drew',   handler:'@drew',    time:'5 hr',    tweet:'Pellentesque nibh lorem, bibendum vitae nunc eu, sodales sagittis nisi.', comments:'1,000', retweets: '550', likes:'1,250.500'},
  {src:'./src/assets/profile-3.png', name:'Owen',   handler:'@owen',    time:'12.3 hr', tweet:'Sed urna enim, dapibus in vestibulum ut, maximus non est. Nam eu ante enim.', comments:'1,000', retweets: '550', likes:'1,250.500'},
  {src:'./src/assets/profile-3.png', name:'Owen',   handler:'@owen',    time:'12.3 hr', tweet:'Sed urna enim, dapibus in vestibulum ut, maximus non est. Nam eu ante enim.', comments:'1,000', retweets: '550', likes:'1,250.500'},
]);


const id = ref('home');
const dropdown = ref(false);
</script>

<template>
  <div id="app" class="flex container h-screen w-full">
    <div class="lg:w-1/5 lpx-2 lg:px-6 py-2 border-r border-lighter  flex flex-col justify-between">
      
      
      <div class="">
          <button class="h-12 w-12 hover:bg-lightblue text-3lx rounded-full text-blue">
            <i class="fab fa-twitter"></i>
          </button>

          <div>
            <button v-for="(tab, i) in TabItems" :key="i" @click="id = tab.id" 
            :class="`focus:outline-none hover:text-blue flex items-center py-2 px-4 hover:bg-lightblue rounded-full mr-auto ${id === tab.id ? 'text-blue' : ''}`">
              <i :class="`${tab.icon} text-2xl mr-4 text-left`"></i>
              <p class="hidden lg:block text-lg font-semibold text-left"> {{tab.title}} </p>
            </button>
          </div>

          <button class="text-white bg-blue rounded-full font-semibold focus:outline-none lg:w-full lg:h-auto w-12 h-12 p-3 hover:bg-darkblue">
            <p class="hidden lg:block">Tweet</p>
            <i class="fas fa-plus lg:hidden"></i>
          </button>
      </div>


      <div class="lg:w-full relative">
        <button @click="dropdown = true" class="flex items-center w-full hover:bg-lightblue rounded-full p-2 focus:outline-none">
          <img src="./assets/profile.jpg" alt="" class="w-12 h-12 rounded-full">
          <div class="ml-4 hidden lg:block">
            <p class="text-sm font-bold leading-tight">Anıl Gündal</p>
            <p class="text-sm leading-tight">@anilgundal</p>
          </div>
          <i class="hidden lg:block fas fa-angle-down ml-auto text-lg"></i>
        </button>
       
       
        <div v-if="dropdown === true" class="absolute bottom-0 left-0 w-64 rounded-lg shadow-md border-lightest bg-white mb-16">
          <button @click="dropdown = false" class="flex items-center w-full hover:bg-lightest focus:outline-none p-3">
            <img src="./assets/profile.jpg" alt="" class="w-12 h-12 rounded-full">
            <div class="ml-4">
              <p class="text-sm font-bold leading-tight">Anıl Gündal</p>
              <p class="text-sm leading-tight">@anilgundal</p>
            </div>
            <i class="fas fa-check ml-auto text-blue"></i>
          </button>
          <button @click="dropdown = false" class="w-full text-left hover:bg-lightest border-t border-lighter focus:outline-none text-sm p-3">
            Add an existing account 
          </button>
          <button @click="dropdown = false" class="w-full text-left hover:bg-lightest border-t border-lighter focus:outline-none text-sm p-3">
            Logout @anilgundal
          </button>
        </div>
      </div>
    </div>

    <!-- Tweet Böümü -->
    <div class="w-1/2 h-full overflow-y-scroll">
      <div class="px-5 py-3 border-b border-lighter flex items-center justify-between">
        <h1 class="text-xl font-bold">Home</h1>
        <i class="far fa-star text-xl text-blue"></i>
      </div>
      <div class="px-5 py-3 border-b-8 border-lighter flex">
          <div class="">
            <img src="./assets/profile.jpg" alt="Anıl Gündal" class="w-12 h-12 rounded-full">
          </div>
          <form class="w-full px-4 relative">
            <textarea class="w-full focus:outline-none mt-3 pb-3" placeholder="What's up?"></textarea>
            <div class="flex items-center">
              <i class="text-lg text-blue mr-4 far fa-image"></i>
              <i class="text-lg text-blue mr-4 fas fa-film"></i>
              <i class="text-lg text-blue mr-4 far fa-chart-bar"></i>
              <i class="text-lg text-blue mr-4 far fa-smile"></i>
            </div>
            <button class="h-10 px-4 text-white font-semibold bg-blue hover:bg-darkblue focus:outline-none rounded-full absolute bottom-0 right-0">
              Tweet
            </button>
          </form>
      </div>

      <div class="flex flex-col-reverse">
        <!-- Tweet Lists -->
      <div v-for="(follow, i) in followers" :key="i" class="w-full p-4 border-b hover:bg-lighter flex">
        <div class="flex-none mr-4">
          <img :src="`${follow.src}`" class="h-12 w-12 rounded-full flex-none" alt="">
        </div>
        <div class="w-full">
            <div class="flex items-center w-full">
              <p class="font-semibold"> {{ follow.name }} </p>
              <p class="text-sm text-dark ml-2"> {{ follow.handle }} </p>
              <p class="text-sm text-dark ml-2"> {{ follow.time }} </p>
              <i class="fas fa-angle-down text-dark ml-auto"></i>
            </div>
            <p class="py-2">{{ follow.tweet }}</p>
            <div class="flex items-center justify-between w-full">
              <div class="flex items-center text-sm text-dark">
                <i class="far fa-comment mr-3"></i>
                <p>{{ follow.comments }}</p>
              </div>
              <div class="flex items-center text-sm text-dark">
                <i class="fas fa-retweet mr-3"></i>
                <p>{{ follow.retweets }}</p>
              </div>
              <div class="flex items-center text-sm text-dark">
                 <i class="fas fa-heart mr-3"></i>
                <p>{{ follow.likes }}</p>
              </div>
              <div class="flex items-center text-sm text-dark">
                <i class="fas fa-share-square mr-3"></i>
              </div> 
            </div>
        </div>
      </div>
      </div>
      

    </div>

    <!-- Trending bölümü -->
    <div class="md:block hidden w-1/3 h-full border-l border-lighter py-2 px-6 overflow-y-scroll relative">
      
      <!-- Search Tweets -->
      <input class="pl-12 text-sm rounded-full w-full p-2 bg-lighter"  placeholder="Search Twitter">
      <i class="fas fa-search absolute left-0 top-0 mt-4 ml-12 text-sm text-light"></i>
      
      <!-- Trending Tweets -->
      <div class="w-full rounded-lg bg-lightest p-3 my-4">
        <div class="flex items-center justify-between p-3">
          <p class="text-lg font-bold">Trends for you</p>
          <i class="fas fa-cog text-lg text-bold text-blue"></i>
        </div>
        <button v-for="(trend, i) in trending" :key="i" class="w-full flex justify-between hover:bg-lighter p-3 border-t border-lighter">
          <div>
            <p class="text-sm text-left leading-tight text-dark"> {{ trend.top }} </p>
            <p class="font-bold text-left leading-tight"> {{ trend.title }} </p>
            <p class="text-left leading-tight text-dark"> {{ trend.bottom }} </p>
          </div>
          <i class="fas fa-angle-down text-lg text-dark"></i>
        </button>
        <button class="p-3 w-full hover:bg-ligter text-left text-blue border-t border-lighter">
          Show more
        </button>
      </div>


      <!-- Who to follow -->
      <div class="w-full rounded-lg bg-lightest p-3 my-4">
        <div class="p-3">
          <p class="text-lg font-bold">Who to Follow</p>
        </div>
        <button v-for="(friend,i) in friends" :key="i"  class="w-full flex  hover:bg-lighter p-3 border-t border-lighter">
         <img :src="`${friend.src}`" alt="" class="w-12 h-12 rounded-full">
          <div class="hidden lg:block ml-4">
            <p class="text-sm font-bold leading-tight">{{ friend.name }}</p>
            <p class="text-sm leading-tight">{{ friend.handle }}</p>
          </div>
          <button class="ml-auto text-sm text-blue py-2 px-4 rounded-full border-2 border-blue">Follow</button>
        </button>
        <button class="p-3 w-full hover:bg-ligter text-left text-blue border-t border-lighter">
          Show more
        </button>
      </div>
    </div>


  </div>
</template>

