<template>
  <div>
    <br>
    <b-container fluid>
      <b-row class="col-sm row justify-content-end" >     
        <b-button size="sm" variant="success" @click="gotoParam('AgencyStageEdit',{updateFlag:true})">編輯</b-button>&ensp; 
        <b-button size="sm" variant="danger" @click="deleteCheck()">刪除</b-button>&ensp; 
        <b-button size="sm" variant="outline-secondary" @click="gotoParam('OpenPeriodDetail')">回上一頁</b-button>
      </b-row>
    </b-container>
    <br>
    <stageSimplyInfo/>
    <br>
    <agencyStageDetailInfo/>
  </div>
</template>


<script>
import agencyStageDetailInfo from './AgencyStageDetailInfo.vue'
import stageSimplyInfo from './StageSimplyInfo.vue'
export default {
  data(){
    return{
     
  }
 },
 methods:  {
    reset(){

    },
    add(){

    },
    update(){

    }
  },
  components:{
    agencyStageDetailInfo,stageSimplyInfo
  },
}
</script>
<style>
.col-md-2 {
  background-color: rgb(50, 91, 224);
  color: white;
  text-align: left;
}

</style>