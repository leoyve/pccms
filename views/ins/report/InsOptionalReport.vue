<template>
	<div>
		<br>
		<h3><strong>督工通報案件自選欄位查詢</strong></h3>
		<br>
		<b-container fluid>
			<b-form-row>
				<b-form-group class="col-md-12" label-cols-md="3" content-cols-md="9" label="通報案件編號關鍵字" label-align-md="right">
					<b-form-input type="search"></b-form-input>
				</b-form-group>
			</b-form-row>
			<b-form-row>
				<b-form-group class="col-md-12" label-cols-md="3" content-cols-md="9" label="通報工程名稱關鍵字" label-align-md="right">
					<b-form-input type="search"></b-form-input>
				</b-form-group>
			</b-form-row>
			<b-form-row>
				<b-form-group class="col-md-12" label-cols-md="3" content-cols-md="9" label="通報缺失地點關鍵字" label-align-md="right">
					<b-form-input type="search"></b-form-input>
				</b-form-group>
			</b-form-row>
			<b-form-row>
				<b-form-group class="col-md-12" label-cols-md="3" content-cols-md="9" label="通報案件主題關鍵字" label-align-md="right">
					<b-form-input type="search"></b-form-input>
				</b-form-group>
			</b-form-row>
			<b-form-row>
				<b-form-group class="col-md-12" label-cols-md="3" content-cols-md="9" label="通報案件具體內容關鍵字" label-align-md="right">
					<b-form-input type="search"></b-form-input>
				</b-form-group>
			</b-form-row>
			<b-form-row>
				<b-form-group class="col-md-12" label-cols-md="3" content-cols-md="9" label="通報日期" label-align-md="right">
					<b-container>
						<b-row>
							<b-col><b-form-datepicker id="example-datepicker1" v-model="value1" class="mb-2"></b-form-datepicker></b-col>~
							<b-col><b-form-datepicker id="example-datepicker2" v-model="value2" class="mb-2"></b-form-datepicker></b-col>
						</b-row>
					</b-container>
				</b-form-group>
			</b-form-row>
			<b-form-row>
				<b-form-group class="col-md-12" label-cols-md="3" content-cols-md="9" label="分案情形" label-align-md="right">
					<b-form-radio-group v-model="check2" :options="checkAssign" name="radio-validation-1"></b-form-radio-group>
				</b-form-group>
			</b-form-row>
			<b-form-row>
				<b-form-group class="col-md-12" label-cols-md="3" content-cols-md="9" label="結案情形" label-align-md="right">
					<b-form-radio-group v-model="check3" :options="checkClosed" name="radio-validation-2"></b-form-radio-group>
				</b-form-group>
			</b-form-row>
			<b-form-row>
				<b-form-group class="col-md-12" label-cols-md="3" content-cols-md="9" label="納入督工有效統計案件" label-align-md="right">
					<b-form-radio-group v-model="check2" :options="checkAssign2" name="radio-validation-1"></b-form-radio-group>
				</b-form-group>
			</b-form-row>
			<b-form-row>
				<b-form-group class="col-md-12" label-cols-md="3" content-cols-md="9" label="通報方式" label-align-md="right">
					<b-form-select :options="type"></b-form-select>
				</b-form-group>
			</b-form-row>
			<b-form-row>
				<b-form-group class="col-md-12" label-cols-md="3" content-cols-md="9" label="顯示項目" label-align-md="right">
					<b-form-checkbox-group
						v-model="selected"
						:options="checkOptions"
						class="mb-2"
						value-field="item"
						text-field="name"
						disabled-field="notEnabled"
						name="flavour-1a"
						inline
					></b-form-checkbox-group>
				</b-form-group>
			</b-form-row>
			<b-form-row class="justify-content-end">
				<b-button size="sm" variant="success" @click="report()" >產生報表</b-button>&nbsp;&nbsp;
				<b-button size="sm" variant="outline-secondary" @click="reset">清除</b-button>
			</b-form-row>
		</b-container>
		<br>
	</div>
</template>


<script>


export default {
 data(){
	return{
		checkAssign:	[
			{	value: '', text: '全部'	},
			{	value: 'N', text: '未分案'	},
			{	value: 'Y', text: '已分案'	},
		],
		checkClosed:	[
			{	value: '', text: '全部'	},
			{	value: 'N', text: '未結案'	},
			{	value: 'E', text: '逾期未結案'	},
			{	value: 'W', text: '待審查結案'	},
			{	value: 'Y', text: '已結案'	},
		],
		checkAssign2:[
			{	value: 'Y', text: '是'	},
			{	value: 'N', text: '否'	},
			{	value: '', text: '不限'	},
		],
		type: [
			{ value: '', text: '' , disabled: true},
			{ value: '0', text: '電話' },
			{ value: '1', text: '傳真' },
			{ value: '2', text: '線上網路' },
			{ value: '3', text: '智慧型手機' },
			{ value: '4', text: '行動版通報' },
			{ value: '5', text: '信件' },
			{ value: '6', text: '媒體' },
		],
	checkOptions: [
      {	name:	'案件編號',	item:	'1',  },
      {	name:	'通報日期',	item:	'2',  },
      {	name:	'通報方式',	item:	'3',  },
      {	name:	'性別',	item:	'4',  },
      {	name:	'通報主題',	item:	'5',  },
      {	name:	'具體內容',	item:	'6',   },
      {	name:	'工程類別',	item:	'7',   },
      {	name:	'施工告示牌標示通報工程名稱',	item:	'8',   },
      {	name:	'標案系統標案編號',	item:	'9',   },
      {	name:	'標案名稱',	item:	'10',   },
      {	name:	'...',	item:	'11',   },
      {	name:	'處理情形',	item:	'12',   },
      {	name:	'民眾滿意度',	item:	'13',   },
      {	name:	'考核結果',	item:	'14',   },
    ],
	}
 },
 methods: {
	report(){
		alert("報表下載");
	}
 },
}

</script>

<style>
.col-form-label {
  background-color: #737373;
  color: white;
  font-weight: bolder;
}
</style>