<template>
    <div>
        <base-card>
            <base-button @click="changeTab('add-resource')" :mode="addResButtonMode">Add Resource</base-button>
            <base-button @click="changeTab('stored-resources')" :mode="storedResButtonMode">Stored Resources</base-button>
        </base-card>
    </div>
    <keep-alive>
        <component :is="selectedTab"></component>
    </keep-alive>
</template>

<script>
    import StoredResources from './StoredResources.vue';
    import AddResource from './AddResource.vue';
    export default{
        components:{
            StoredResources,
            AddResource,
        },
        data(){
            return{
                selectedTab: 'stored-resources',
                savedResources:[],
            }
        },
        provide(){
            return{
                savedResources: this.savedResources,
                submitData: this.submitData,
                deleteData: this.deleteData,

            }
        },
        computed:{
            storedResButtonMode(){
                return this.selectedTab === 'stored-resources' ? null : 'flat';
            },

            addResButtonMode(){
                return this.selectedTab === 'add-resource' ? null : 'flat';
            }
        },
        methods:{
            changeTab(cmp){
                this.selectedTab = cmp;
            },
            submitData(title, description, link){
                const newResource = {
                    id: new Date().toISOString(),
                    title: title,
                    description: description,
                    link: link,
                }

                this.savedResources.unshift(newResource);
                this.selectedTab ='stored-resources';
            },
            deleteData(index){
                const resId = this.savedResources.findIndex(res => res.id === index); 
                this.savedResources.splice(resId, 1); /* (res => res.id === index) for every res is savedResources returns first element which satisfies 
                                                        the expression in arrow function. So it will return res.id which is equal to index being received as argument from LearningResources.vew*/
            }

        },

    }
</script>

<style scoped>
    
</style>
