<template>
    <div class="mid-list">
        <conItem v-for="(itm,idx) in listData" :key="idx" :itmData="itm"/>
    </div>
</template>
<script>
    import conItem from '@/components/sub-comps/con-item.vue'
    import {mapState} from 'vuex'
    export default{
        name:'mid-list',
        components:{
            conItem
        },
        computed: {
          ...mapState({
            listData: state => state.indexData.flowResult,
          })
        },
        created () {
            this.$store.dispatch('setPageStatus',1)
            this.$store.dispatch('setIndexData')
        },
        watch:{
            listData(val){
                this.$store.dispatch('setPageStatus',2)
                this.listData = val
            }
        }
    }
</script>
<style lang="scss">
    .mid-list{
        box-sizing:border-box;
        margin:0 30px;
    }
</style>