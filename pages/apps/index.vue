<template>
    <div class="w-full flex flex-col md:flex-row flex-wrap items-stretch justify-center py-10">
        <div class="w-full flex flex-wrap items-center justify-center" >
            <lottie :options="defaultOptions" :height="400" :width="400" v-on:animCreated="handleAnimation"/>
        </div>
        <div class="max-w-4xl px-6 lg:px-10 py-10 flex flex-wrap relative items-start justify-center">
            <div class="w-full h-16 flex flex-wrap items-center justify-start mb-10">
                <span class="font-bold text-2xl md:text-4xl text-blue-600" v-scroll-reveal="{ mobile: false, origin: 'top', easing: 'cubic-bezier(0.5, 0, 0, 1)', distance: '80px'}">Apps</span>
                <span class="flex-auto bg-gray-600 self-center ml-3" style="height:0.5px;"></span>
            </div>
            <div class="w-full grid grid-cols-1 md:grid-cols-2 gap-4">
                <div v-scroll-reveal="{ mobile: false, origin: 'bottom', easing: 'cubic-bezier(0.5, 0, 0, 1)', distance: '180px'}" v-for="(app, i) in apps" :key="i" class="w-full rounded-lg duration-300 transition-all flex flex-col items-stretch justify-start shadow-xl bg-white">
                    <div class="w-full self-stretch flex flex-wrap items-center justify-center py-5 rounded-t-md md:rounded-t-lg card-img" v-lazy-container="{ selector: 'img' }">
                        <img :data-src="`${app.path}/display.svg`"
                            :data-loading="`${app.path}/display.svg?lqip`"
                            class="w-40 flex rounded-t-md md:rounded-t-lg" :alt="app.title">
                    </div>
                    <div class="px-8 pb-4 rounded-b-md md:rounded-b-lg w-full felx-1 felx items-stretch justify-start">
                        <div class="w-full flex flex-wrap justify-between items-center text-lg text-gray-600 font-light py-3">
                            <p class="font-normal">APP</p>
                            <p>{{app.reseaseDate | year}}</p>
                        </div>
                        <h2 class="text-2xl font-bold text-gray-800">{{app.title}}</h2>
                        <p class="text-lg text-gray-700 leading-tight my-2" style="-webkit-box-orient: vertical;-webkit-line-clamp: 2;line-height:1.5rem; max-height: 3rem;overflow: hidden;white-space: normal;text-overflow: ellipsis;-o-text-overflow: ellipsis;">{{app.description | desc}}</p>
                        <div class="text-sm font-medium mt-4 flex flex-wrap justify-between items-stretch self-stretch">
                            <div class="flex flex-wrap items-center justify-center gap-x-3" v-lazy-container="{ selector: 'img' }">
                                <svg class=" w-10 h-10 inline-block fill-current" viewBox="0 0 380 380"><circle cx="190" cy="190" r="190" fill="#FFEDEF"/><mask id="a" width="380" height="380" x="0" y="0" maskUnits="userSpaceOnUse"><circle cx="190" cy="190" r="190" fill="#FFEDEF"/></mask><g mask="url(#a)"><g clip-path="url(#clip0)"><path fill="#F9C9B6" stroke="#000" stroke-width="4" d="M244 386.5c-14.4-20-25.7-58.7-27-78L148.5 279 120 386.5h124z"/><mask id="b" width="124" height="118" x="120" y="279" maskUnits="userSpaceOnUse"><path fill="#AC6651" d="M244 396.5c-14.4-20-25.7-68.7-27-88L148.5 279 120 396.5h124z"/></mask><g mask="url(#b)"><ellipse cx="214" cy="277" fill="#000" rx="59" ry="54"/></g><mask id="c" fill="#fff"><path fill-rule="evenodd" d="M273.9 218a43.9 43.9 0 00-.2-.8l-16.4-68.4v-.2-.2l-.1-.3A77.7 77.7 0 00106 184.3l17 71A77.7 77.7 0 00274 219l-.2-1z" clip-rule="evenodd"/></mask><path fill="#F9C9B6" fill-rule="evenodd" d="M273.9 218a43.9 43.9 0 00-.2-.8l-16.4-68.4v-.2-.2l-.1-.3A77.7 77.7 0 00106 184.3l17 71A77.7 77.7 0 00274 219l-.2-1z" clip-rule="evenodd"/><path fill="#000" d="M273.9 218l-4 .8h.1l3.9-.9zm-.2-.8l-3.9 1 4-1zm-16.4-68.4l-3.9 1 4-1zm0-.4l-4 1 4-1zm-.1-.3l3.8-1-.9-3.8-3.9.9 1 3.9zm0 0l-4 1 1 3.8 3.9-1-1-3.8zm-93.6-57l-1-3.9 1 4zM106 184.3l1 3.9 3.8-1-1-3.8-3.8.9zm0 0l-1-3.9-3.8 1 .9 3.8 3.9-1zm17 71l-4 .8 1 4 4-1-1-3.9zm0 0l3.9-1.1-1-3.8-3.8 1 .9 3.8zm93.3 56l-.9-4 1 4zm57.8-92.3l-.9-3.9-3.8 1 .8 3.8 4-.9zm0 0l1 3.9 3.9-1-1-3.8-3.9.9zm3.7-2l-.1-.4-7.8 1.9v.3l7.9-1.8zm-.1-.4v-.3l-7.9 1.9.1.3 7.8-1.9zm-24.3-66.9l16.4 68.5 7.8-2-16.4-68.3-7.8 1.8zm7.8-1.8v-.3l-7.8 2v.1l7.8-1.8zm0-.3v-.2l-7.9 2v.1l7.9-1.8zm-8 1.4l.1.3 7.8-1.9v-.3l-7.8 2zm4.9 3l-1.9-7.8 1.9 7.8zm3-4.9a81.7 81.7 0 00-98.5-59.9l2 7.8a73.7 73.7 0 0188.7 54l7.7-1.9zm-98.5-59.9a81.7 81.7 0 00-60.5 98l7.8-1.8A73.7 73.7 0 01164.5 95l-1.8-7.8zm-55.7 101l-1.8-7.8 1.8 7.8zm20 66l-17-70.8-7.8 1.8 17 71 7.8-2zm-4.8-2.9l1.8 7.8-1.8-7.8zm-3 5a81.7 81.7 0 0098.2 58.9l-1.9-7.8a73.7 73.7 0 01-88.5-53.2l-7.8 2zm98.2 58.9a81.7 81.7 0 0060.7-97l-7.8 1.7a73.7 73.7 0 01-54.8 87.5l1.9 7.8zm56-100.1h-.1l1.9 7.8-1.9-7.8zm-3.3 3.7l.3 1.1 7.7-1.8-.2-1.1-7.8 1.8z" mask="url(#c)"/></g><path fill="#9287FF" stroke="#000" stroke-width="4" d="M187.8 363.6l1.2-1.6-1.2 1.6 1.7 1.3 1.2-1.8h0v-.2l.2-.1a64.2 64.2 0 013.2-4.6c2.2-2.9 5.3-6.7 9-10.5 3.6-3.8 7.8-7.4 12.1-10a20 20 0 0112.5-3.2c42.5 5.7 73.7 24.5 94 52.5H48.4c16.3-29.3 39.5-48 77-56.6a15 15 0 016.5.4c2.7.6 5.8 1.7 9.1 3.2 6.7 2.9 14 7.1 21 11.5a356.2 356.2 0 0125.6 18h.1z"/><path fill="#E0DDFF" stroke="#000" stroke-width="4" d="M113.6 333l5.2-19.1c.2-.8 1.2-1 1.7-.5a46.6 46.6 0 0039.9 15c.8-.2 1.5.8 1 1.5l-13 25a1 1 0 01-1.1.5c-4-.9-23.6-5.7-33.6-21.5a1 1 0 010-.8zM244.2 333l-11.6-19.5c-.4-.7-1.3-.7-1.8 0a38.6 38.6 0 01-19 14.1c-.7.2-1 1-.6 1.5l13.5 22.8c.2.4.6.6 1 .5 2-.7 9.4-3.7 18.5-18.4a1 1 0 000-1z"/><path fill="#000" stroke="#000" stroke-linejoin="round" stroke-width="4" d="M170.5 350.5l-9-21.5-7 15 16 6.5zM202 349.5l9-21.5 7 15-16 6.5zM131.5 310l-12 3 10 6.5 2-9.5zM221 310l11 3-7 6.5-4-9.5z"/><path fill="#171921" stroke="#171921" stroke-width="4" d="M236.8 262.2a34 34 0 001.1-11.9 3 3 0 00-4-2.5c-4.3 1.7-18.3 7-28.1 8.3-10.9 1.5-27.3-.3-32-.9a3 3 0 00-3.3 3.5 34 34 0 0066.3 3.5z"/><mask id="d" width="68" height="40" x="172" y="249" maskUnits="userSpaceOnUse"><path fill="#171921" d="M235.8 249.2a32 32 0 11-63.5 7.9l63.5-8z"/></mask><g mask="url(#d)"><circle cx="208.5" cy="289.3" r="21.5" fill="#FC909F" transform="rotate(-7 208.5 289.3)"/></g><path fill="#000" d="M268.7 104c-9 39.7-107.5 43.6-127.3 43.3-52.1 5-28.2 67.9-19.2 99.2-7.5.9-6.6 9.9-34.4-62.1-22.2-57.6 44-91.3 93-102.3s68-27.4 68-27.4c20.6 8.9 25.2 25.7 19.9 49.3z"/><path fill="#000" d="M262.4 177.4l-15-53.7 10.3-9c10 37.3 10.2 58.8 4.7 62.7zM136.5 220.3c-5.1-27.3-19.3-22.6-28.6-21.5l-9.3-44.1 40.7-7.8c.8-.3 1.6-.4 2.5-.5l-2.5.5c-18.2 5.5-6.5 52.2 8.2 71.6l-11 1.8zM83.2 116.8c9-4.3 19.4-1.6 23.4.3l-12 14.7c3.1-4.8-6.3-12-11.4-15z"/><path fill="#000" d="M68 133.7c11.7-6.6 22.9-4.2 27-2L90.2 147c-1-8.4-15.3-12.4-22.2-13.3z"/><path fill="#171921" fill-rule="evenodd" d="M163.3 200c.1.9 1.1 1 1.7.5a19.6 19.6 0 0118-4.4c.7.2 1.5-.5 1.2-1.2a10.8 10.8 0 00-21 5.2zM227.4 190c.1.9 1.1 1 1.7.5A19.4 19.4 0 01247 186c.7.2 1.5-.4 1.2-1.2a10.7 10.7 0 00-20.7 5v.2z" clip-rule="evenodd"/><path stroke="#171921" stroke-width="8" d="M124.1 199.6c-2.4-.3-5-.2-7.5.3-10.3 2.1-17.3 10.2-13.9 21.8 3.5 12 11.8 14.9 22 12.8a19.6 19.6 0 006.6-2.6"/><path fill="#F9C9B6" d="M131.7 231.6c-2 1.3-4.4 2.4-7 2.9-10.2 2-18.5-.8-22-12.8-3.4-11.6 3.6-19.7 14-21.8 3-.6 6.1-.6 9 0l6 31.7z"/><path stroke="#171921" stroke-width="4" d="M122.7 207.3c-4.3-1-13.1-.1-14.1 11.1M112.5 210c2.5 1.3 7.6 6 8.5 14"/><path stroke="#000" stroke-linecap="round" stroke-width="4" d="M228 167.2c5.7-2.7 19-5 27 6.5M152.6 192.5c2-5.9 9.7-17.1 23.5-14.7"/><path stroke="#171921" stroke-width="4" d="M209 201.1a51.4 51.4 0 0010.6 23.7s-2.6 6.5-12.8 6"/></g><defs><clipPath id="clip0"><path fill="#fff" d="M0 0h200v320H0z" transform="translate(90 67)"/></clipPath></defs></svg>
                                <span class="text-lg text-blue-700">{{app.author}}</span>
                            </div>
                            <nuxt-link :to="`${app.path}/`" class="btn-secondary focus:shadow-outline">
                                Read More
                                <svg class="w-5 h-5 inline-block ml-1 fill-current" viewBox="0 0 24 24"><path fill-rule="evenodd" d="M12.7 4.3a1 1 0 10-1.4 1.4l5.3 5.3H5a1 1 0 100 2h11.6l-5.3 5.3a1 1 0 001.4 1.4l7-7c.4-.4.4-1 0-1.4l-7-7z" clip-rule="evenodd"/></svg>
                            </nuxt-link>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import Lottie from '@/components/apps/lottie.vue';
import animationData from '@/static/json/idea_anim.json';
export default {
    layout: 'apps',
    components:{
        'lottie': Lottie,
    },
    data(){
        return{
            defaultOptions: {animationData, animationData }
        }
    },
    async asyncData({ $content, params }) {
        const apps = await $content('apps').fetch()
        return { apps }
    },
    filters:{
        desc: val=>{
            let str_arrs = val.split(" ");
            str_arrs.shift();
            let capitalize = (s) => {
                if (typeof s !== 'string') return ''
                return s.charAt(0).toUpperCase() + s.slice(1).toLowerCase()
            }
            return capitalize(val.split(" ")[0]) + " " + str_arrs.join(" ").toLowerCase();
        },
        date: val=>{
            const monthNames = ["Jan", "Feb", "Mar", "Apr", "May", "Jun",
                                "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"
                                ];
            let new_date = new Date(val);
            return new_date.getDate() + " " + monthNames[new_date.getMonth()] + " " + new_date.getFullYear();
        },
        year: val=>{
            let new_date = new Date(val);
            return new_date.getFullYear();
        }
    },
    methods:{
        handleAnimation: function (anim) {
            this.anim = anim;
        },
        img: (path)=>{
            return `~/static/apps/${path}/display.svg`;
        },
        imgLazy: (path)=>{
            return `~/static/apps/${path}/display.svg?webp?lqip`;
        }
    },
    computed:{
        
    }
}
</script>
<style lang="scss" scoped>
.filter-img{
    filter: hue-rotate(20deg);
}

.min\:h-10{
    min-height: 2.5rem;
} 

.min\:w-10{
    min-width: 2.5rem;
}

.max\:h-10{
    max-height: 12rem;
    overflow: hidden;
}

.btn-secondary{
    @apply bg-transparent text-gray-600 p-1 rounded-md text-lg font-semibold flex flex-wrap justify-center items-center text-center transition-all duration-300;
    transition: all 0.4s;
    & > svg {
        @apply ml-0 transition-all duration-300;
    }

  &:hover{
    @apply transition-all duration-300 ease-in-out text-gray-500;
    & > svg {
        @apply ml-2 transition-all duration-300;
    }
  }

  &:focus{
    @apply transition-all duration-300 ease-in-out outline-none shadow-outline text-gray-500;
    & > svg {
        @apply ml-2 transition-all duration-300;
    }
  }
}

.btn-primary{
  @apply bg-transparent text-base flex flex-wrap justify-center items-center text-center;
  color: rgba(47, 140, 246, 0.7);
  transition: all 0.4s;

  &:hover{
    @apply transition-all duration-300 ease-in-out outline-none;
    color: rgba(47, 140, 246, 0.9);
  }
}

.card-img{
    background: rgb(109,170,252);
    background: linear-gradient(138deg, rgba(109,170,252,1) 0%, rgba(183,153,255,1) 100%);
    transition: all 0.6s ease-in;
    @apply flex flex-wrap items-stretch justify-center;

    img{
        height: 10rem;
    }
}
</style>