<script>
	import { TabulatorFull as Tabulator } from 'tabulator-tables';
	import { onMount } from 'svelte';

	let table = null;
	let columnIdForGreenRowColor = [1, 2, 4, 5];
	let columnIdForBoldedFont = [1, 2, 3, 4, 5, 6];
	let firstPeriod = '12/2019';
	let secondPeriod = '12/2020';
	let thirdPeriod = '12/2021';
	let forthPeriod = '12/2022';
	let tableData = [
		{
			id: 1,
			assets: 'A. UPISANI A NEUPLAĆENI KAPITAL (UNPAID SUBSCRIBED CAPITAL)',
			firstPeriod: '',
			firstPeriodPercent: '',
			secondPeriod: '',
			thirdPeriod: '',
			forthPeriod: ''
		},
		{
			id: 2,
			assets: 'B. STALNA IMOVINA (FIXED ASSETS)',
			firstPeriod: '',
			firstPeriodPercent: '',
			secondPeriod: '',
			thirdPeriod: '',
			forthPeriod: ''
		},
		{
			id: 3,
			assets: 'V. ODLOŽENA PORESKA SREDSTVA (DEFERRED TAX LIABILITIES)',
			firstPeriod: '',
			firstPeriodPercent: '',
			secondPeriod: '',
			thirdPeriod: '',
			forthPeriod: ''
		},
		{
			id: 4,
			assets: 'G. OBRTNA IMOVINA (WORKING CAPITAL)',
			firstPeriod: '',
			firstPeriodPercent: '',
			secondPeriod: '',
			thirdPeriod: '',
			forthPeriod: '',
			_children: [
				{
					id: 1.1,
					assets: 'I Zalihe (Inventories)',
					firstPeriod: '',
					firstPeriodPercent: '',
					secondPeriod: '',
					thirdPeriod: '',
					forthPeriod: ''
				},
				{
					id: 1.2,
					assets: 'II Potraživanja po osnovu prodaje (Trade receivables)',
					firstPeriod: '',
					firstPeriodPercent: '',
					secondPeriod: '',
					thirdPeriod: '',
					forthPeriod: ''
				},
				{
					id: 1.3,
					assets: 'III Potraživanja iz specifičnih poslova (Specific receivables)',
					firstPeriod: '',
					firstPeriodPercent: '',
					secondPeriod: '',
					thirdPeriod: '',
					forthPeriod: ''
				},
				{
					id: 1.4,
					assets: 'IV Druga potraživanja (Other receivables)',
					firstPeriod: '',
					firstPeriodPercent: '',
					secondPeriod: '',
					thirdPeriod: '',
					forthPeriod: ''
				},
				{
					id: 1.5,
					assets:
						'V Finansijska sredstva koja se vrednuju po fer vrednosti kroz bilans uspeha (Financial assets carried at fair value through P&L)',
					firstPeriod: '',
					firstPeriodPercent: '',
					secondPeriod: '',
					thirdPeriod: '',
					forthPeriod: ''
				},
				{
					id: 1.6,
					assets: 'VI Kratkoročni finansijski plasmani (ST financial placements)',
					firstPeriod: '',
					firstPeriodPercent: '',
					secondPeriod: '',
					thirdPeriod: '',
					forthPeriod: ''
				},
				{
					id: 1.7,
					assets: 'VII Gotovinski ekvivalenti i gotovina (Cash and cash equivalent)',
					firstPeriod: '',
					firstPeriodPercent: '',
					secondPeriod: '',
					thirdPeriod: '',
					forthPeriod: ''
				},
				{
					id: 1.8,
					assets: 'VIII Porez na dodatu vrednost (Value added tax)',
					firstPeriod: '',
					firstPeriodPercent: '',
					secondPeriod: '',
					thirdPeriod: '',
					forthPeriod: ''
				},
				{
					id: 1.9,
					assets: 'IX Aktivna vremenska razgraničenja (Payments and accrued income)',
					firstPeriod: '',
					firstPeriodPercent: '',
					secondPeriod: '',
					thirdPeriod: '',
					forthPeriod: ''
				}
			]
		},
		{
			id: 5,
			assets: 'UKUPNA AKTIVA/TOTAL ASSETS',
			firstPeriod: '',
			firstPeriodPercent: '',
			secondPeriod: '',
			thirdPeriod: '',
			forthPeriod: ''
		},
		{
			id: 6,
			assets: 'D. VANBILANSNA AKTIVA/OFF BALANCE ASSETS',
			firstPeriod: '',
			firstPeriodPercent: '',
			secondPeriod: '',
			thirdPeriod: '',
			forthPeriod: ''
		}
	];

	//FUNCTIONS
	// function formatColumns(cell, formatterParams, onRendered) {
	// 	cell.getElement().style.backgroundColor = '#E2EFDA'; // Set the background color
	// 	return cell.getValue(); // Return the cell value
	// }
	//END OF FUNCTIONS

	onMount(() => {
		table = new Tabulator('#BilansStanja', {
			layout: 'fitColumns',
			columnHeaderVertAlign: 'middle',
			data: tableData,
			dataTree: true,
			dataTreeStartExpanded: true,
			rowFormatter: function (row) {
				//console.log(row.getData());
				if (columnIdForGreenRowColor.includes(row.getData().id)) {
					row.getElement().style.backgroundColor = '#92D050';

					//row.getElement().style.border = '1px solid lightgray';
					// const children = row.getElement().childNodes;
					// children.forEach((child) => {
					// 	child.style.backgroundColor = '#92D050';
					// 	child.style.border = '1px solid lightgray';
					// 	//console.log(child.textContent);
					// });
				}
				if (columnIdForBoldedFont.includes(row.getData().id)) {
					row.getElement().style.fontWeight = 'bold';

					// const children = row.getElement().childNodes;
					// children.forEach((child) => {
					// 	child.style.fontWeight = 'bold';
					// });
				}
				row.getElement().style.borderTop = '1px solid #808080';
			},
			columns: [
				{
					title: 'AKTIVA/ASSETS',
					field: 'assets',
					width: 400,
					headerSort: false,
					headerHozAlign: 'center',
					formatter: 'textarea',
					editor: 'input'
				},
				{
					title: firstPeriod,
					field: 'firstPeriod',
					width: 150,
					headerSort: false,
					headerHozAlign: 'center',
					columns: [
						{ title: 'zvaničan', headerSort: false, headerHozAlign: 'center', editor: 'input' }
					]
				},
				{
					title: '% of total',
					field: 'firstPeriodPercent',
					width: 100,
					headerSort: false,
					cssClass: 'custom-header-cell',
					headerHozAlign: 'center',
					// formatter: formatColumns,
					editor: 'input'
				},
				{
					title: secondPeriod,
					field: 'firstPeriod',
					width: 150,
					headerSort: false,
					headerHozAlign: 'center',
					columns: [
						{ title: 'zvaničan', headerSort: false, headerHozAlign: 'center', editor: 'input' }
					]
				},
				{
					title: '% of total',
					field: 'secondPeriodPercent',
					width: 100,
					headerSort: false,
					cssClass: 'custom-header-cell',
					headerHozAlign: 'center',
					// formatter: formatColumns,
					editor: 'input'
				},
				{
					title: thirdPeriod,
					field: 'firstPeriod',
					width: 150,
					headerSort: false,
					headerHozAlign: 'center',
					columns: [
						{ title: 'zvaničan', headerSort: false, headerHozAlign: 'center', editor: 'input' }
					],
					editor: 'input'
				},
				{
					title: '% of total',
					field: 'thirdPeriodPercent',
					width: 100,
					headerSort: false,
					cssClass: 'custom-header-cell',
					headerHozAlign: 'center',
					// formatter: formatColumns,
					editor: 'input'
				},
				{
					title: forthPeriod,
					field: 'forthPeriod',
					width: 150,
					headerSort: false,
					headerHozAlign: 'center',
					columns: [
						{ title: 'nezvaničan', headerSort: false, headerHozAlign: 'center', editor: 'input' }
					]
				},
				{
					title: '% of total',
					field: 'forthPeriodPercent',
					width: 100,
					headerSort: false,
					cssClass: 'custom-header-cell',
					headerHozAlign: 'center',
					// formatter: formatColumns,
					editor: 'input'
				}
			]
		});
	});
</script>

<section>
	<div id="Wrapper">
		<h1>Bilans stanja</h1>
		<div id="BilansStanja" />
	</div>
</section>

<style>
	section {
		flex: 1;
	}

	#Wrapper {
		padding: 0 10px;
		margin: 0;
	}

	:global(.custom-header-cell) {
		background-color: #E2EFDA!important; /* Change the background color of the header cells */
	}

	/* .tabulator .tabulator-row .tabulator-cell[tabulator-field='firstPeriodPercent'] {
		background-color: '#E2EFDA';
	} */

	/* .tabulator .tabulator-row .tabulator-cell[tabulator-field='firstPeriodPercent'] {
		background-color: #E2EFDA!important;
	} */
</style>
