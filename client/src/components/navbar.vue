<template>
    <div>
        <div v-if="page === 2 || page === 3" class="root">
            <div class="left">
                <div class="box">
                    <a href="" @click.prevent="gotosecondpage"><i class="fas fa-globe-asia fa-1x"> Published</a>
                </div>
                <div class="box">
                    <a href="" @click.prevent="gotothirdpage">Draft</a>
                </div>
            </div>
            <div class="right">
                <div class="box">
                    <a href="" @click.prevent="gotofourthpage"><i class="fas fa-feather-alt"></i> Write.</a>
                </div>
                <div class="box">
                    <a @click.prevent="logout" href="">Sign out</a>
                </div>
            </div>
        </div>
        <div v-else-if="page === 4" class="root">
            <div class="left">
                <div class="box">
                    <a href="" @click.prevent="gotosecondpage"><i class="fas fa-globe-asia fa-1x"> Published</a>
                </div>
                <div class="box">
                    <a href="" @click.prevent="gotothirdpage">Draft</a>
                </div>
            </div>
            <div class="right">
                <div class="box">
                    <a href="" @click.prevent="publish(false)">Save to draft</a>
                </div>
                <div class="box">
                    <a href="" @click.prevent="publish(true)">Publish</a>
                </div>
                <div class="box">
                    <a @click.prevent="logout" href="">Sign out</a>
                </div>
            </div>
        </div>
        <div v-else-if="page === 5" class="root">
            <div class="left">
                <div class="box">
                    <a href="" @click.prevent="gotosecondpage"><i class="fas fa-globe-asia fa-1x"> Published</a>
                </div>
                <div class="box">
                    <a href="" @click.prevent="gotothirdpage">Draft</a>
                </div>
            </div>
            <div class="right">
                <div class="box">
                    <a href="" @click.prevent="gotoeditpage"><i class="fas fa-feather-alt"></i> Edit.</a>
                </div>
                <div class="box">
                    <a @click.prevent="logout" href="">Sign out</a>
                </div>
            </div>
        </div>        
        

    </div>
</template>

<script>
export default {
    props: ['page'],
    data: function(){
        return {

        }
    },
    methods: {
        publish(value){
            this.$emit('publish', value)
        },
        gotofourthpage(){
            this.$emit('gotofourthpage')
        },
        gotosecondpage(){
            this.$emit('gotosecondpage')
        },
        logout(){
            if(gapi.auth2){
                var auth2 = gapi.auth2.getAuthInstance();
                    auth2.signOut().then(function () {
                    console.log('User signed out.');
                });            
            }
            localStorage.removeItem('token')
            this.$emit('gotofirstpage')

        },
        gotothirdpage(){
            this.$emit('gotothirdpage')
        },
        gotoeditpage(){
            
            this.$emit('gotoeditpage')
        }
        
    }
}
</script>

<style scoped>
    a{
        text-decoration-line: none;
    }
    a:hover{
        border-bottom: 2px solid white;
    }
    * {
        color: white;
        font-family: 'Roboto', sans-serif;
    }
    .root {
        background-color: #016087;
        height: 6vh;
        width: 100vw;
        display: flex;
        justify-content: space-between;
        align-items: center
    }
    .left, .right{
        display: flex;
    }
    .right .box {
        padding-right: 2vw;
    }
    .left .box {
        padding-left: 2vw;
    }
</style>