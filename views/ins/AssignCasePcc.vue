<template>
  <div>
    <br>
    <b-container fluid>
      <b-container>
        <b-row>
          <b-col class="col-md-2 "><font color="red">*</font>主管機關</b-col>
          <b-col ><b-form-select v-model="statusPicked" :options="wkut"></b-form-select></b-col>
        </b-row>
        <b-row>
          <b-col class="col-md-2 ">副知機關</b-col>
          <b-col ><b-form-select v-model="statusPicked" :options="wkut"></b-form-select></b-col>
        </b-row>
        <b-row>
          <b-col class="col-md-2 "><font color="red">*</font>限辦日期</b-col>
          <b-col ><b-form-datepicker id="example-datepicker1" v-model="value1" class="mb-2"></b-form-datepicker></b-col>
        </b-row>
        <b-row>
          <b-col class="col-md-2 ">標案管理系統工程名稱</b-col>
          <b-col ><b-form-input :disabled="disabledFlag"></b-form-input></b-col>
        </b-row>
        <b-row>
          <b-col class="col-md-2 ">工程類別</b-col>
          <b-col ><b-form-select v-model="statusPicked" :options="category" :disabled="disabledFlag"></b-form-select></b-col>
        </b-row>
        <b-row>
          <b-col class="col-md-2 ">允許本案免需上傳改善照片</b-col>
          <b-col >
            <b-form-radio-group v-model="check1" :options="check" name="radio-validation" :disabled="disabledFlag"></b-form-radio-group>
          </b-col>
        </b-row>
      </b-container>
      <br>
      <b-container>
        <b-row class="col-sm row justify-content-start">
          <b-button size="sm" variant="info" @click="queryCmdCase()" >查詢所屬標案</b-button>&ensp; 
          <b-button size="sm" variant="info" @click="queryNearby()" >檢視鄰近通報地點標案位置圖</b-button>&ensp; 
        </b-row>
        <b-row class="col-sm row justify-content-center"> 
          <b-button size="sm" variant="success" @click="queryHandler" >分文</b-button>&ensp; 
          <b-button size="sm" variant="outline-secondary" @click="gotoParam('CaseAssignQuery')">取消</b-button>
        </b-row>
      </b-container>
      <br>
      <h2 class="text-left"><font color="red">通報案件基本資料</font></h2>
      <br>
      <caseVue :test="'不可編輯'" :disabledFlag="true"/>
      <br>
    </b-container>
    <br>
    <h2 class="text-center"><font color="red">通報缺失位置地圖</font></h2>
    <br>
    <caseMapInfoVue/>
    <br>
    <casePhotoInfoVue/>
  </div>
</template>


<script>
import caseVue from './CaseInfo.vue'
import caseMapInfoVue from './CaseMapInfo.vue'
import casePhotoInfoVue from './CasePhotoInfo.vue'

export default {
  data(){
    return{
      wkut: [
        { value: '1', text: '內政部-陳XX'},
        { value: '1', text: '法務部-林XX'},
        { value: '1', text: '行政院-陳XX'},
        { value: '1', text: '台北市政府-吳XX'},
        { value: '1', text: '國防部-劉XX'},
        { value: '1', text: '財政部-張XX'},
      ],
      category: [
        { value: '1', text: '機電工程'},
        { value: '2', text: '水電工程' },
        { value: '3', text: '空調工程' },
        { value: '4', text: '防漏工程' },
        { value: '6', text: '電梯工程' },
        { value: '7', text: '隧道工程' },
      ],
      check: [
        { value: 'Y', text: '是'},
        { value: 'N', text: '否' },
      ],
  }
 },
 methods:  {
    queryCmdCase(){
      //新開視窗
      let routeUrl = this.$router.resolve({name:'CmdCaseQuery'})
      window.open(routeUrl.href, '_blank'); 

    },
    queryNearby(){
      let routeUrl = this.$router.resolve({name:'NearbyCase'})
      window.open(routeUrl.href, '_blank'); 
    },
  },
  components: {
    caseVue,
    caseMapInfoVue,
    casePhotoInfoVue
  },
}
</script>
<style>

</style>