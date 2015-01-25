# thaiprovinces
Angular Module which helps create a form which lookup Thailand's Province, District and Subdistrct purely from client side.

Related Blog Post (in Thai): http://coresharp.net/blog/provincelookup

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">ThaiProvinces</span> by <a xmlns:cc="http://creativecommons.org/ns#" href="http://nant.co" property="cc:attributionName" rel="cc:attributionURL">Jirawat Padungkijjanont</a> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.<br />Based on a work at <a xmlns:dct="http://purl.org/dc/terms/" href="https://github.com/nantcom/thaiprovinces" rel="dct:source">https://github.com/nantcom/thaiprovinces</a>.

#Sample

Sample Usage with https://github.com/angular-ui/ui-select :

```html
  <ui-select
             ng-model="object.Address_State"
             theme="bootstrap"
             on-select="ctrl.thaiprovinces.setProvince($item.name)"
             reset-search-input="true">
      <ui-select-match placeholder="ระบุจังหวัด...">{{$select.selected.name}}</ui-select-match>
      <ui-select-choices repeat="item.name as item in thaiprovinces.all | filter: { name: $select.search }">
          <span>{{item.name}}</span>
      </ui-select-choices>
  </ui-select>
  
  <ui-select ng-model="object.Address_District"
             theme="bootstrap"
             on-select="ctrl.thaiprovinces.setDistrict($item.name)"
             reset-search-input="true">
      <ui-select-match placeholder="ระบุอำเภอ (เขต)...">{{$select.selected.name}}</ui-select-match>
      <ui-select-choices repeat="item.name as item in thaiprovinces.districtList | filter: { name: $select.search }">
          <span>{{item.name}}</span>
      </ui-select-choices>
  </ui-select>
  
  <ui-select ng-model="object.Address_Subdistrict"
             theme="bootstrap"
             reset-search-input="true">
      <ui-select-match placeholder="ระบุตำบล (แขวง)...">{{$select.selected.name}}</ui-select-match>
      <ui-select-choices repeat="item.name as item in thaiprovinces.subDistrictList | filter: {name : $select.search}">
          <span>{{item.name}}</span>
      </ui-select-choices>
  </ui-select>                
```

*Module Javascript Code:

```javascript
  (function () {
  
      var module = angular.module('myMod', ['ui.bootstrap', 'ui.select', 'nantcom-thaiprovinces']);
  
      module.controller("myCtrl", function ($scope, $rootScope, thaiprovinces) {
  
          $scope.thaiprovinces = thaiprovinces; // for binding
          this.thaiprovinces = thaiprovinces; // for setting cascade list of district/subdistrict
  })();
```
