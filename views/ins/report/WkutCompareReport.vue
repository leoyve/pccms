<template>
	<div>
		<br>
		<h3><strong>機關案件考核自評填寫統計表</strong></h3>
		<br>
		<b-container fluid>
			<b-form-row>
				<b-form-group class="col-md-12" label-cols-md="3" content-cols-md="9" label="通報案件限辦日期" label-align-md="right">
					<b-container>
						<b-row>
							<b-col><b-form-datepicker id="example-datepicker1" v-model="value1" class="mb-2"></b-form-datepicker></b-col>~
							<b-col><b-form-datepicker id="example-datepicker2" v-model="value2" class="mb-2"></b-form-datepicker></b-col>
						</b-row>
					</b-container>
				</b-form-group>
			</b-form-row>
			<b-form-row>
				<b-form-group class="col-md-12" label-cols-md="3" content-cols-md="9" label="機關類別" label-align-md="right">
					<b-form-radio-group v-model="check2" :options="checkClosed" name="radio-validation-1"></b-form-radio-group>
				</b-form-group>
			</b-form-row>
			<b-form-row class="justify-content-end">
				<b-button size="sm" variant="success" @click="queryHandler" >查詢</b-button>&nbsp;
				<b-button size="sm" variant="outline-secondary" @click="reset">清除</b-button>
			</b-form-row>
		</b-container>
		<br>
		<div>
			<b-container fluid>
				<b-form-row class="justify-content-center text-light bg-primary"><h4><strong>機關案件考核自評填寫統計表</strong></h4></b-form-row>
				<b-form-row class="justify-content-end">
				<b-table striped hover :items="items" :fields="fields" head-variant="warning">
					<template #cell(finish)="row">
						<a href="#" variant="primary" @click="gotoParam('ReportCommonList', row.item)" >{{row.item.finishNum}}</a>
					</template>
					<template #cell(unFinish)="row">
						<a href="#" variant="primary" @click="gotoParam('ReportCommonList', row.item)" >{{row.item.unFinishNum}}</a>
					</template>
				</b-table>
				</b-form-row>
				<b-pagination align="right"
					v-model="currentPage"
					:total-rows="rows"
					:per-page="perPage"
					first-number
				></b-pagination>
			</b-container>
		</div>

	</div>
</template>

<script>

export default {
 data(){
	return{
		rows: 100,
		perPage: 1,
		currentPage: 1,
		// 這邊有給KEY的話，items也要換成KEY，否則取值會是undefined，這邊是要顯示的欄位，不顯示的放在ITEMS裡面就好
		fields: [
			{
				key:	'id',
				label:	'流水號'
			},
			{
				key:	'wkut',
				label:	'主管機關',
			},
			{
				key:	'caseNum',
				label:	'結案件數'
			},
			{
				key:	'finish',
				label:	'完成考核自評件數'
			},
			{
				key:	'unFinish',
				label:	'未完成考核自評件數'
			},
			{
				key:	'rate',
				label:	'完成考核算評比例(%)'
			},
			

		],
		items:	[
			//待分文要顯示紅字，結案日期也是
			{ id: 1, wkut: '宜蘭縣政府', caseNum:'10',	finishNum: '5', unFinishNum: '2',	rate:'100.00%',	pk: 5566 },
			{ id: 2, wkut: '台中市政府', caseNum:'5',	finishNum: '0', unFinishNum: '1',	rate:'33.33%',	pk: 5566 },
			{ id: 3, wkut: '新北市政府', caseNum:'6',	finishNum: '2', unFinishNum: '0',	rate:'66.67%',	pk: 5566 },
		],
		checkAssign:	[
			{	value: '', text: '是'	},
			{	value: 'N', text: '否'	},
			{	value: 'Y', text: '不限'	},
		],
		checkClosed:	[
			{	value: '', text: '全部'	},
			{	value: 'N', text: '主管'	},
			{	value: 'E', text: '主辦'	},
		],
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