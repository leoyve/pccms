<template>
	<div>
		<br>
		<h3><strong><font color="brown">通報案件查處情形公告一覽表</font></strong></h3>
		<br>
		<b-container >
			<b-form-row>
				<b-form-group class="col-md-12" label-cols-md="3" content-cols-md="9" label="通報案件編號關鍵字" label-align-md="right">
					<b-input type="search"></b-input>
				</b-form-group>
			</b-form-row>
			<b-form-row>
				<b-form-group class="col-md-12" label-cols-md="3" content-cols-md="9" label="通報公共設施名稱關鍵字" label-align-md="right">
					<b-input type="search"></b-input>
				</b-form-group>
			</b-form-row>
			<b-form-row>
				<b-form-group class="col-md-12" label-cols-md="3" content-cols-md="9" label="通報案件主題關鍵字" label-align-md="right">
					<b-input type="search"></b-input>
				</b-form-group>
			</b-form-row>
			<b-form-row>
				<b-form-group class="col-md-12" label-cols-md="3" content-cols-md="9" label="通報日期" label-align-md="right">
					<b-container>
						<b-row>
							<b-col><b-form-datepicker id="example-datepicker3" v-model="value3" class="mb-2"></b-form-datepicker></b-col>~
							<b-col><b-form-datepicker id="example-datepicker4" v-model="value4" class="mb-2"></b-form-datepicker></b-col>
						</b-row>
					</b-container>
				</b-form-group>
			</b-form-row>
			<b-form-row class="justify-content-end">
				<b-button size="sm" variant="success"  @click="queryHandler" >查詢</b-button>&nbsp;
                <b-button size="sm" variant="outline-secondary" @click="reset">清除</b-button>
			</b-form-row>
		</b-container>
		<br>
		
		<div>
			<b-container fluid>
				<b-form-row class="justify-content-center text-light bg-primary"><h4><strong>通報案件查處結果公告一覽表</strong></h4></b-form-row>
				<b-form-row class="justify-content-end">
					<b-table striped hover :items="items" :fields="fields" head-variant="light">
					</b-table>
					<b-pagination align="right"
						v-model="currentPage"
						:total-rows="rows"
						:per-page="perPage"
						first-number
					></b-pagination>
				</b-form-row>
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
				key:	'serial',
				label:	'流水號'
			},
			{
				key:	'caseNum',
				label:	'通報案件編號'
			},
			{
				key:	'submitDate',
				label:	'通報日期',
			},
			{
				key:	'constName',
				label:	'通報公共設施名稱',
				thStyle: { width: "12%" },
			},
			{
				key:	'address',
				label:	'所在縣市及地點'
			},
			{
				key:	'topic',
				label:	'通報主題'
			},
			{
				key:	'category',
				label:	'設施類別',
				thStyle: { width: "8%" },
			},
			{
				key:	'wkut',
				label:	'查處機關'
			},
			{
				key:	'desc',
				label:	'查處說明'
			},
			{
				key:	'isFa',
				label:	'是否納入閒置系統列管'
			},
			{
				key:	'reason',
				label:	'不納入列管原因'
			},
			{
				key:	'action',
				label:	''
			},
		],
		items:	[
			{	caseNum:'10200000002', submitDate:'102/11/14',constName:'金門國家公園範圍內道路約3公里長的路燈安裝好迄今未亮與破損,有礙行車安全',
			wkut: '內政部', address:'[金門縣] 金門縣 金寧鄉寧湖路', topic:'	道路路燈安裝好迄今未亮與破損,有礙行車安全',category:'交通建設(停車場、機場、觀光遊憩、道路、橋樑、漁港等)',
			desc:'移督工系統處理。',isFa:'不納入閒置系統列管',reason:'其他不納入列管'},
			{	caseNum:'10200000005', submitDate:'102/12/26',constName:'北濱海水浴場',
			wkut: '花蓮縣政府農業處', address:'[花蓮縣] 花蓮縣花蓮市海濱街', topic:'	花蓮北濱海水浴場荒廢閒置無使用過',category:'交通建設(停車場、機場、觀光遊憩、道路、橋樑、漁港等)',
			desc:'',isFa:'納入閒置系統列管',reason:''},
		]
	}
 },
 methods: {
	
 },
 mounted(){
	this.items.forEach((items, index) => { items.serial = index + 1; });
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