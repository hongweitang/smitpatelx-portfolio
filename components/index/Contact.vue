<template>
    <section class="w-full min-h-screen flex flex-wrap justify-center items-center mt-5 lg:mt-0 p-4 lg:p-32 mb-32" id="contact">
        <div class="flex flex-wrap justify-center items-center">
            <h2 v-scroll-reveal="{ delay: 700, mobile: false, origin: 'bottom', easing: 'cubic-bezier(0.5, 0, 0, 1)', distance: '80px'}" class="w-full text-gray-700 text-3xl md:text-4xl font-semibold leading-tight text-center">
                <span class="mr-3 text-blue-600 text-base lg:text-2xl font-medium font-mono leading-tight self-end">04.</span>
                Lets get in touch
            </h2>
            <form v-scroll-reveal="{ delay: 1000, mobile: false, origin: 'bottom', easing: 'cubic-bezier(0.5, 0, 0, 1)', distance: '80px'}" method="post" @submit.prevent="formSubmission" class="flex flex-wrap flex-col mt-8 w-full maxw-50 px-6">
                <div class="w-full grid grid-cols-1 lg:grid-cols-2 gap-4 my-2">
                    <div class="flex flex-wrap flex-col">
                        <label for="email" class="font-mono text-base text-blue-600 mb-2 w-full">Email</label>
                        <input tabindex="1" required class="w-full form-input" minlength="6" maxlength="50" type="email" name="email" id="email" v-model="email" placeholder="eg. xyz@gmail.com">
                    </div>
                    <div class="flex flex-wrap flex-col">
                        <label for="phone" class="font-mono text-base text-blue-600 mb-2 w-full">Phone</label>
                        <div class="grid grid-cols-8 relative w-full gap-x-2">
                            <Country class="flex flex-col items-stretch justify-center col-span-2 focus-within:shadow-outline" v-on:countrySelected="onCountrySelect"/>
                            <input tabindex="4" required class="inline-block col-span-6 form-input" type="tel" pattern="[0-9]{10}" maxlength="10" name="phone" id="phone" v-model="phone" placeholder="eg. 000-000-0000">
                        </div>
                    </div>
                </div>
                <div class="w-full grid grid-cols-2 gap-4 my-2">
                    <div class="flex flex-wrap flex-col">
                        <label for="first_name" class="font-mono text-base text-blue-600 mb-2 w-full">First Name</label>
                        <input tabindex="5" required class="w-full form-input" minlength="2" maxlength="15" type="text" name="first_name" id="first_name" v-model="first_name" placeholder="eg. Smit">
                    </div>
                    <div class="flex flex-wrap flex-col">
                        <label for="last_name" class="font-mono text-base text-blue-600 mb-2">Last Name</label>
                        <input tabindex="6" required class="w-full form-input" minlength="2" maxlength="15" type="text" name="last_name" id="last_name" v-model="last_name" placeholder="eg. Patel">
                    </div>
                </div>
                <div class="w-full grid grid-cols-1 md:grid-cols-2 gap-4 my-2">
                    <div class="flex flex-wrap flex-col">
                        <label for="business_name" class="font-mono text-base text-blue-600 mb-2">Business Name</label>
                        <input tabindex="7" required class="w-full form-input" minlength="5" maxlength="30" type="text" name="business_name" id="business_name" v-model="business_name" placeholder="eg. Google LLC.">
                    </div>
                    <div class="flex flex-wrap flex-col relative">
                        <label for="no_of_employee" class="font-mono text-base text-blue-600 mb-2">No. of Employee</label>
                        <s-select :tabindex="8" :options="employee_options"></s-select>
                        <!-- <select tabindex="8" required class="w-full custom_select form-input" minlength="5" maxlength="30" type="text" name="no_of_employee" id="no_of_employee" v-model="no_of_employee">
                            <option value="" default disabled>Select No. of Employee</option>
                            <option value="2">upto 2</option>
                            <option value="10">upto 10</option>
                            <option value="50">upto 50</option>
                            <option value="100">upto 100</option>
                            <option value="500">upto 500</option>
                            <option value="1000">upto 1000</option>
                            <option value="1000plus">1000+</option>
                        </select> -->
                    </div>
                </div>
                <div class="w-full flex flex-wrap flex-col my-2" >
                    <label for="est_budget" class="font-mono text-base text-blue-600 mb-2 flex">Estimated budget: <span class="text-lg ml-1">{{est_budget_f}}</span></label>
                    <div class="w-full flex flex-wrap flex-col relative">
                        <input tabindex="9" required step="500" class="focus:outline-none z-40" min="3000" max="200000" value="`${est_budget}`" type="range" name="est_budget" id="est_budget" v-model="est_budget">
                        <div class="slider_progress absolute h-2 w-1/2 z-0 rounded mt-2" :style="`width:${(est_budget*100/200000)-1}%`"></div>
                    </div>
                </div>
                <div class="w-full flex flex-wrap flex-col mt-4 mb-2 pr-2" >
                    <label for="message" class="font-mono text-base text-blue-600 mb-2">Additional Message</label>
                    <textarea tabindex="10" class="form-input" rows="5" maxlength="2000" type="text" name="message" id="message" v-model="message" placeholder="Start typing ..."/>
                </div>
                <div class="w-full flex flex-wrap flex-row my-2 pr-2 pt-6 justify-between" >
                    <button tabindex="11" class="mb-10 focus:outline-none focus:shadow-outline form_button" type="submit">
                        Send
                        <svg class="w-4 h-4 fill-current text-blue-600 inline-block ml-3" viewBox="0 0 24 24"><path fill-rule="evenodd" clip-rule="evenodd" d="M22.7071 1.293c.3905.3904.3905 1.0236 0 1.4141l-11 11c-.3905.3906-1.0237.3906-1.4142 0-.3905-.3905-.3905-1.0237 0-1.4142l11-11c.3905-.3905 1.0237-.3905 1.4142 0z" /><path fill-rule="evenodd" clip-rule="evenodd" d="M22.7071 1.293c.2716.2716.3637.6748.2368 1.0374l-7 20a1.0001 1.0001 0 01-1.8577.0758l-3.8438-8.6486-8.6485-3.8438a1 1 0 01.0757-1.8576l20.0001-7a1 1 0 011.0374.2367zM4.7111 9.1105l6.695 2.9756a1 1 0 01.5077.5077l2.9756 6.6951L20.37 3.63 4.711 9.1106z" /></svg>
                    </button>
                    <button tabindex="12" class="mb-10 ml-3 focus:outline-none focus:shadow-outline form_button2" @click.prevent="reset" type="button">
                        Reset
                        <svg class="w-4 h-4 fill-current text-blue-600 inline-block ml-3" viewBox="0 0 24 24"><path fill-rule="evenodd" clip-rule="evenodd" d="M18.7071 5.2929c.3905.3905.3905 1.0237 0 1.4142l-12 12c-.3905.3905-1.0237.3905-1.4142 0-.3905-.3905-.3905-1.0237 0-1.4142l12-12c.3905-.3905 1.0237-.3905 1.4142 0z" /><path fill-rule="evenodd" clip-rule="evenodd" d="M5.2929 5.2929c.3905-.3905 1.0237-.3905 1.4142 0l12 12c.3905.3905.3905 1.0237 0 1.4142-.3905.3905-1.0237.3905-1.4142 0l-12-12c-.3905-.3905-.3905-1.0237 0-1.4142z"/></svg>
                    </button>
                </div>
            </form>
        </div>
    </section>
</template>
<script>
import { CollapseTransition } from 'vue2-transitions'
import Country from '@/components/index/Country.vue'
import SSelect from '@/components/library/SSelect.vue'

export default {
    components:{
        Country,
        CollapseTransition,
        SSelect
    },
    data(){
        return {
            email:'',
            first_name:'',
            last_name:'',
            business_name:'',
            est_budget:10000,
            message:'',
            no_of_employee:'',
            phone:'',
            country:'ca',
            ip_address:'',
            employee_options:[
                {val:'2', text:'Upto 2'},
                {val:'10', text:'Upto 10'},
                {val:'50', text:'Upto 50'},
                {val:'100', text:'Upto 100'},
                {val:'500', text:'Upto 500'},
                {val:'1000', text:'Upto 1000'},
                {val:'1000plus', text:'1000+'},
            ]
        }
    },
    computed:{
        est_budget_f:{
            get(){
                var formatter = new Intl.NumberFormat('en-US', {
                    style: 'currency',
                    currency: 'USD',
                    minimumFractionDigits: 0
                });
                return formatter.format(this.est_budget);
            },
            set(val){
                this.est_budget=val;
            }
        }
    },
    asyncData (context) {
        return context.env
    },
    methods: {
        formSubmission(){
            if(this.ip_address == ""){
                this.getIp();
            } {
                this.submit();
            }
        },
        async submit(){
            await this.$axios.$post(`${process.env.API_URL}/api/v1/contact`,
            {
                first_name: this.first_name,
                last_name: this.last_name,
                email: this.email,
                phone: this.phone,
                country_code: this.country,
                business_name: this.business_name,
                business_employees: this.no_of_employee,
                est_budget: this.est_budget,
                message: this.message,
                ip_address: this.ip_address
            })
            .then(res=>{
                alert('Thank you for contacting me!')
                this.reset();
            })
            .catch(err=>{
                console.error(err)
            })
        },
        reset(){
            this.email=''
            this.first_name=''
            this.last_name=''
            this.business_name=''
            this.est_budget=10000
            this.message=''
            this.no_of_employee=''
            this.phone=''
            this.country='ca'
        },
        onCountrySelect(val){
            this.country = val;
        },
        async getIp() {
            await this.$axios.$get('https://json.geoiplookup.io/')
            .then(res=>{
                this.ip_address = res.ip;
                this.submit()
            }).catch(error=>{
                console.log('Error getting ip: ',error);
            });
        }
    },
    created() {
    },
}
</script>
<style lang="scss" scoped>
@import url('@/assets/scss/contact.scss');
</style>