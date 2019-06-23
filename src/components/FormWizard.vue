
<template>
    <div>
        <ul class="steps has-content-centered is-small">
            <li class="steps-segment" v-for="tab in tabs" :class="{ 'is-active': tab.isActive }" v-bind:key="tab.name">
                <span class="steps-marker">{{tab.num}}</span>
                <div class="steps-content">
                    <p>{{tab.info}}</p>
                </div>
            </li>
        </ul>                    
        <div class="tab-details">
            <slot :formData="formData"></slot>
        </div>
        <br/>
        <div class="field is-grouped">
            <div class="control" v-if="currentActive > 0">
                <button @click="previousTab()" class="button is-primary">Previous</button>
            </div>
            <div class="control" v-if="currentActive < totalTabs - 1">
                <button @click="nextTab()" class="button is-link">Next</button>
            </div>
            <div class="control" v-if="currentActive == totalTabs -1" >
                <button @click="submit()" class="button is-success">Submit</button>
            </div>
        </div>
                
    </div>
</template>


<script>


export default {
  name: 'form-wizard',
  
  data(){
    return{
        tabs: [],
        currentActive: 0,
        totalTabs: 0,
        formData:{
            header1: '',
            header2: '',
            header3: '',
            header4: '',
            header5: '',
            header6: '',
            references1: '',
            references2: '',
            references3: '',
            references4: '',
            timeZone: '',
            taskOrg: '',
            situation1: '',
            situation2: '',
            situation3: '',
            situation4: '',
            situation5: '',
            enemy1: '',
            friendly1: '',
            friendly2: '',
            friendly3: '',
            friendly4: '',
            friendly5: '',
            friendly6: '',
            friendly7: '',
            friendly8: '',
            friendly9: '',
            friendly10: '',
            friendly11: '',
            friendly12: '',
            friendly13: '',
            mission1:'',
            execution1:'',
            execution2:'',
            execution3:'',
            execution4:'',
            execution5:'',
            sustainment1:'',
            sustainment2:'',
            sustainment3:'',
            sustainment4:'',
            sustainment5:'',
            commandAndSignal1:'',
            commandAndSignal2:'',
            commandAndSignal3:'',
            commandAndSignal4:'',
            commandAndSignal5:''
     }
        
    }
   },

    created(){
        this.tabs = this.$children;
        
    },

    mounted(){
        this.totalTabs = this.tabs.length;
        console.log("number of tabs: "+this.totalTabs)
    },

    methods:{

        previousTab(){
            this.currentActive--;
            this.tabs.forEach(tab => {
                tab.isActive = false;
            });
                this.tabs[this.currentActive].isActive = true;

        },

        nextTab(){
            //Validate input
            this.$root.$validator.validate('step'+(this.currentActive+ 1)+'.*').then(valid => {
                if (valid){
                    this.currentActive++;
                    this.tabs.forEach(tab => {
                        tab.isActive = false;
                    });
            
                    this.tabs[this.currentActive].isActive = true;
                }
            }); 

        },

        submit(){
            
            this.$root.$validator.validate('step'+this.totalTabs+'.*').then(valid => {
                if (valid){
                    alert("Everything passes ! Ready to Submit")
                }
            });
        }  
    }
}
</script>


<style>
</style>