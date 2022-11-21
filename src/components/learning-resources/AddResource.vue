<template>
        <base-dialog v-if="inputIsInvalid" title="Invalid Input" @close="confirmError">
            <template #default>
                <p>Unfortunately, at least one input field is empty</p>
                <p>Close this window and try again</p>
            </template>
            <template #actions>
                <base-button @click="confirmError">Close</base-button>
            </template>
        </base-dialog>
        <base-card>
        <form @submit.prevent="saveResource">
                <div class="form control">
                    <label for="title">Title</label>
                    <input id="title" name="title" type="text" ref="title"/>
                </div>
                <div class="form control">
                    <label for="description">Description</label>
                    <textarea  id="description" name="description" rows="3" ref="description"></textarea>
                </div>
                <div class="form control">
                    <label for="link">Link</label>
                    <input id="link" name="link" type="url" ref="link" />
                </div>
                <div>
                    <base-button mode="flat">Save Resource</base-button>
                </div>              
            </form>
        </base-card>
</template>

<script>
    export default{
        inject:['submitData'],
        data(){
            return{
                inputIsInvalid: false,
            }
        },
        methods:{
            saveResource(){
                const enteredTitle = this.$refs.title.value;
                const enteredDescription = this.$refs.description.value;
                const enteredLink = this.$refs.link.value;

                if(enteredTitle.trim()===''||
                    enteredDescription.trim()===''||
                    enteredLink.trim()===''){
                        this.inputIsInvalid = true;
                        return;
                    }

                this.submitData(enteredTitle, enteredDescription, enteredLink);
            },

            confirmError(){
                this.inputIsInvalid = false;
            }
        }
    }
</script>

<style scoped>
    *{
        box-sizing: border-box;
    }

    div{
        margin-bottom: 1rem;
    }

    label{
        display: block;
        margin-bottom: 0.25rem;
    }

    input, textarea{
        display: block;
        width: 100%;
        padding: 0.15rem;
        border: 1px solid #ccc;
        font: inherit;
    }
    form{
        margin: 1.5rem;
    }
</style>
