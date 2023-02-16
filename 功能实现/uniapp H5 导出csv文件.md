##### 使用XLSX写文件
``` js
import XLSX from 'xlsx';
function export_json_to_csv(arr) {
	console.log("转为csv");	
	// const array = [
	// 	  { A:"S", B:"h", C:"e", D:"e", E:"t", F:"J", G:"S" },
	// 	  { A:  4, B:  5, C:  6, D:  7, E:  8, F:  9, G:  0  }
	// ]
	const jsonWorkSheet = XLSX.utils.json_to_sheet(arr);
	const workBook = {
		SheetNames: ["第一张sheet"],
		Sheets: {
			"第一张sheet": jsonWorkSheet,
		}
	};
	// XLSX.write(wb, write_opts)
	var wbout = XLSX.write(workBook, {
	  bookType: "csv",
	  bookSST: false,
	  type: "binary"
	});
	console.log(wbout)
	return XLSX.writeFile(workBook, "导出表格哦.csv");
};
```
##### 使用vue-json-excel
- 通过点击按钮完成下载
``` js
// main.js
import JsonExcel from "vue-json-excel";
```

``` html
<!-- vue -->
<download-excel
  class="download-csv"
  :data="json_data"
  type="csv"
  name="filename.xls"
  v-show="is_show_download"
>
</download-excel>
<button @click="downloadClick">点我下载</button>
```

``` js
is_show_download: false,
json_data: [
	{
		name: "Tony Peña",
		city: "New York",
		country: "United States",
		birthdate: "1978-03-15"
	},
	{
		name: "TTTT",
		city: "New York",
		country: "United States",
		birthdate: "1978-03-15"
	}
]

downloadClick() {
	document.querySelector(".download-csv").click();
}
```

#### 参考链接
`npm i xlsx@0.16.9`
`npm i vue-json-excel@0.3.0`
`npm i file-saver@2.0.5`
1.[xlsx - npm (npmjs.com)](https://www.npmjs.com/package/xlsx#writing-workbooks)
2.[Writing Files | SheetJS Community Edition](https://docs.sheetjs.com/docs/api/write-options)
3.[vue-json-excel - npm (npmjs.com)](https://www.npmjs.com/package/vue-json-excel)
4.[file-saver - npm (npmjs.com)](https://www.npmjs.com/package/file-saver)
