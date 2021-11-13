<div align="center">
	<h1>CovidVN</h1>
	<h6>(covidvn api)</h6>
	<strong> <i>Trình gói JavaScript cho <a href="https://disease.sh">CovidVN API</a></i></strong><br><br>

![GitHub top language](https://img.shields.io/github/languages/top/disease-sh/node-api)
![Snyk Vulnerabilities for npm scoped package](https://img.shields.io/snyk/vulnerabilities/npm/covidvn)
<!-- ![GitHub package.json version](https://img.shields.io/github/package-json/v/covidvn/node-api) -->
<!-- ![GitHub last commit](https://img.shields.io/github/last-commit/disease-sh/node-api)<br>
![npm bundle size](https://img.shields.io/bundlephobia/minzip/covidvn)
![npm](https://img.shields.io/npm/dw/covidvn)<br>
![GitHub issues](https://img.shields.io/github/issues-raw/disease-sh/node-api)
![License](https://img.shields.io/github/license/disease-sh/node-api) -->
![Profile visits](https://badges.pufler.dev/visits/disease-sh/node-api)

</div>
<br>

## Từ chối các trách nhiệm liên quan
Đây là các dữ liệu liên quan đến COVID-19 được lấy từ API của [Open Disease API](https://disease.sh).

## Cài đặt

[![NPM](https://nodei.co/npm/covidvn.png?downloads=true&downloadRank=true&stars=true)](https://nodei.co/npm/covidvn)

Sử dụng NPM:

```bash
npm i -s covidvn-api
```

## Lưu ý

Chỉ sử dụng package '@aero/centra'.<br>

Tham số **allowNull** hiện có sẵn cho `all`, `countries`, `continents`, `states` và `gov` điểm cuối.
CovidVN-API sắp cật nhập sẽ thêm tham số `vaccine`

## Cách dùng

Tất cả các ví dụ được hiển thị đều sử dụng Promises nhưng cũng có thể chờ/không đồng bộ để tìm nạp dữ liệu bằng CovidVN-API.

### Thêm vào project của bạn 

```js
const api = require('convid-api');

// Bạn có thể chọn URL nào để sử dụng, điều này sẽ không thay đổi hoạt động của API
api.settings({
    baseUrl: 'https://disease.sh' | 'https://api.caw.sh' | 'https://corona.lmao.ninja'
})
```

### Dữ liệu tổng quát

```js
// cái này in ra một bản tóm tắt dữ liệu toàn cầu
api.all().then(console.log)

// cái này in ra một bản tóm tắt dữ liệu toàn cầu với dữ liệu từ ngày vừa qua
api.yesterday.all().then(console.log)

// cái này in ra một bản tóm tắt dữ liệu toàn cầu với dữ liệu từ hai ngày trước
api.twoDaysAgo.all().then(console.log)
```

### Theo quốc gia

```js
// in ra các quốc gia bị nhiễm covid
api.countries().then(console.log) 

// in ra các quốc gia bị nhiễm covid được sắp xếp theo các trường hợp
api.countries({sort:'cases'}).then(console.log) 

// in ra quốc gia cụ thể
api.countries({country:'austria'}).then(console.log) 

// in ra các quốc gia cụ thể
api.countries({country:['austria','china']}).then(console.log) 
```

### Dữ liệu của ngày hôm qua (Theo từng quốc gia)

```js
// in ra các quốc gia bị nhiễm với dữ liệu của từ ngày vừa qua
api.yesterday.countries().then(console.log)

// in ra các quốc gia bị nhiễm với dữ liệu của từ ngày vừa qua được sắp xếp theo các trường hợp
api.yesterday.countries({sort:'cases'}).then(console.log)

// in ra quốc gia cụ thể của từ ngày vừa qua
api.yesterday.countries({country:'austria'}).then(console.log)

// in ra các quốc gia cụ thể của từ ngày vừa qua
api.yesterday.countries({country:['austria','china']}).then(console.log)
```

### Dữ liệu của hai ngày trước (Theo từng quốc gia)

```js
// in ra các quốc gia bị nhiễm với dữ liệu từ hai ngày trước
api.twoDaysAgo.countries().then(console.log)

// in ra các quốc gia bị nhiễm với dữ liệu từ hai ngày trước được sắp xếp theo các trường hợp
api.twoDaysAgo.countries({sort:'cases'}).then(console.log)

// in ra dữ liệu của 1 quốc gia với dữ liệu từ hai ngày trước
api.twoDaysAgo.countries({country:'austria'}).then(console.log)

// in ra dữ liệu quốc gia  với dữ liệu từ hai ngày trước
api.twoDaysAgo.countries({country:['austria','china']}).then(console.log)
```

### Theo Lục địa

```js
// in ra một mảng chứa tất cả các lục địa có người bị nhiễm
api.continents().then(console.log) 

// in ra một mảng của tất cả các lục địa bị nhiễm được sắp xếp theo số trường hợp mắc
api.continents({sort:'cases'}).then(console.log) 

// in ra dữ liệu của một lục địa cụ thể
api.continents({continent:'europe'}).then(console.log)
```

### Dữ liệu của ngày hôm qua (Theo từng lục địa)

```js
// in ra một mảng của tất cả các lục địa bị nhiễm với dữ liệu từ ngày vừa qua
api.yesterday.continents().then(console.log)

// in ra một mảng của tất cả các lục địa bị nhiễm với dữ liệu của từ ngày vừa qua được sắp xếp theo các trường hợp
api.yesterday.continents({sort:'cases'}).then(console.log)

// in ra một lục địa cụ thể với dữ liệu từ ngày vừa qua
api.yesterday.continents({continent:'europe'}).then(console.log)
```

### Dữ liệu của ngày hôm qua (Theo từng quốc gia)

```js
// in ra một mảng của tất cả các lục địa bị nhiễm với dữ liệu từ hai ngày vừa qua
api.twoDaysAgo.continents().then(console.log)

// in ra một mảng của tất cả các lục địa bị nhiễm với dữ liệu của từ hai ngày vừa qua được sắp xếp theo các trường hợp
api.twoDaysAgo.continents({sort:'cases'}).then(console.log)

// in ra một lục địa cụ thể với dữ liệu từ hai ngày vừa qua
api.twoDaysAgo.continents({continent:'europe'}).then(console.log)
```



### JHUCSSE

```js
// in ra một loạt các quốc gia bị nhiễm
api.jhucsse.all().then(console.log)

// in ra một quận của quốc gia bị nhiễm
api.jhucsse.counties().then(console.log)

// in ra một loạt các tỉnh bị nhiễm của một quận cụ thể của quốc gia bị nhiễm
api.jhucsse.counties({county:'abbeville'}).then(console.log)

// in các với các tỉnh của quận cụ thể của quốc gia bị nhiễm
api.jhucsse.counties({county:['abbeville','acadia']}).then(console.log)
```

### Theo dòng thời gian

```js
// in dòng thời gian toàn cầu
api.historical.all().then(console.log)

// in ra dòng thời gian toàn cầu trong 10 ngày qua (use -1 để lấy tất cả dữ liệu)
api.historical.all().then(console.log)

// in ra một loạt các quốc gia bị đánh giá và dòng thời gian của họ
api.historical.countries().then(console.log)

// in ra quốc gia cụ thể và dòng thời gian của họ
api.historical.countries({country:'china'}).then(console.log)

// in ra quốc gia cụ thể và dòng thời gian của họ trong 10 ngày qua (use -1 để lấy tất cả dữ liệu)
api.historical.countries({country:'china', days:10}).then(console.log)

// in một tỉnh cụ thể của một quốc gia cụ thể và dòng thời gian của họ
api.historical.countries({country:'china', province:'hubei'}).then(console.log)

// in một tỉnh cụ thể của một quốc gia cụ thể và dòng thời gian của họ
api.historical.countries({country:'china', province:['hubei','anhui']}).then(console.log)
```

### Mobility Data (Apple)

```js
// in ra một danh sách các tên quốc gia có sẵn
api.apple.countries().then(console.log)

// in ra danh sách các tiểu vùng có sẵn cho một quốc gia cụ thể
api.apple.subregions('austria').then(console.log)

// in dữ liệu di động cho một tiểu vùng cụ thể của một quốc gia, tất cả được sử dụng để truy vấn tổng dữ liệu
api.apple.mobilityData({country:'austria', subregion:'all'}).then(console.log)

// in dữ liệu di động cho nhiều tiểu vùng cụ thể của một quốc gia
api.apple.mobilityData({country:'austria', subregion:['vienna', 'salzburg']}).then(console.log)
```

### Official Government Data

```js
// in ra một danh sách các tên quốc gia có sẵn
api.gov().then(console.log)

// in dữ liệu cho một quốc gia cụ thể
api.gov('austria').then(console.log)
```
