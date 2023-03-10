#### 使用uni-file-picker组件上传文件
- 使用uni-file-picker组件上传文件后，可以得到选择的文件信息，其中包含文件对应的BlobURL
	`tempFilePaths`
	`tempFiles`
#### 读取ObjectURL（BlobURL）
- 向BlobURL发起请求，即可获取地址对应的文件数据
	此处是csv文件的BlobURL，发起网络请求后，得到二进制格式的文件数据
- 使用XLSX读取请求返回的数据，并将其转化为数组对象以及导出为csv文件
	`XLSX 读文件`  `XLSX 写文件`
``` js
import XLSX from 'xlsx';
// "blob:http://localhost:8080/3666975f-a7a3-4f77-a1ba-a6950a41a6a7"
uni.request({
	url:e.tempFilePaths[0],
	success: (res) => {
		import_binary_to_json(res.data);
	}
})

function import_binary_to_json(binary_data) {
	// 读文件 XLSX.read(data, read_opts)
	const wb = XLSX.read(binary_data, {
		type: "binary"
	});
	// 表格数据转为数组对象[{}, {}, {}]
	const json_data = XLSX.utils.sheet_to_json(wb.Sheets[wb.SheetNames[0]]);
	console.log(json_data);
};
```

#### 补充
- 使用uni-file-picker组件上传文件，返回有`tempFilePaths` `tempFiles`数组；取数组中的一个对象`tempFiles[0]`，其`tempFiles[0]["file"]`是一个文件对象
``` js
{
    "tempFiles": [
        {
            "name": "dataformat.json",
            "uuid": 1676625056564,
            "extname": "json",
            "cloudPath": "1676625056563_0.json",
            "url": "blob:http://localhost:8080/c57de9d5-3805-4371-9b32-cf909fedfb37",
            "size": 25119,
            "path": "blob:http://localhost:8080/c57de9d5-3805-4371-9b32-cf909fedfb37",
            "video": {},
            "progress": 0,
            "status": "ready",
            "file": {
                "cloudPath": "1676625056563_0.json",
                "uuid": 1676625056564
            }
        }
    ],
    "tempFilePaths": [
        "blob:http://localhost:8080/c57de9d5-3805-4371-9b32-cf909fedfb37"
    ]
}
```
##### 读取文件对象
``` js
const reader = new FileReader()
reader.readAsText(tempFiles[0]["file"])
// reader.readAsDataURL(file.file)
reader.onload = () => console.log(reader.result)
reader.onerror = () => console.log(reader.error)
```

#### 参考链接
`npm i xlsx@0.16.9`
1.[xlsx - npm (npmjs.com)](https://www.npmjs.com/package/xlsx#writing-workbooks)
2.[Reading Files | SheetJS Community Edition](https://docs.sheetjs.com/docs/api/parse-options)
3.[exif-js/exif.js at 53b0c7c1951a23d255e37ed0a883462218a71b6f · exif-js/exif-js · GitHub](https://github.com/exif-js/exif-js/blob/53b0c7c1951a23d255e37ed0a883462218a71b6f/exif.js#L369)
4.[File - Web API 接口参考 | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Web/API/File)