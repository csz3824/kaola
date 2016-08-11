### 列表接口

	curl http://localhost:3000/base_suppliers.json


### 分页/排序

	curl "http://localhost:3000/base_suppliers.json?page=1"
	curl "http://localhost:3000/base_suppliers.json?page=1&per=100"
	curl "http://localhost:3000/base_suppliers.json?page=1&order=id+desc"

### 查询
#### 等于查询

	curl -g "http://localhost:3000/base_suppliers.json?s[fax]=fax"
	curl -g "http://localhost:3000/base_suppliers.json?s[fax]=fax&page=1&order=id+desc"

#### Like查询
	curl -g "http://localhost:3000/base_suppliers.json?s[like[fax]]=f%25"
	curl -g "http://localhost:3000/base_suppliers.json?s[like[fax]]=f%25&s[fax]=fax&s[old_supplier_id]=abcd"


#### 日期查询
	curl -g "http://localhost:3000/base_suppliers.json?s[date[created_at]]=2016-05-11"
	curl -g "http://localhost:3000/base_suppliers.json?s[date[created_at]]=2016-05-11,2016-05-12"

#### 数值范围查询
	curl -g "http://localhost:3000/base_suppliers.json?s[range[id]]=1,5"
	curl -g "http://localhost:3000/base_suppliers.json?s[range[id]]=,5"
	curl -g "http://localhost:3000/base_suppliers.json?s[range[id]]=3,"

#### 枚举In查询
	curl -g "http://localhost:3000/base_suppliers.json?s[in[id]]=1,2,5"

#### 多表连接的查询
	curl -g "http://scm.laobao.com:9291/tbw_warehouses.json?s[tbc_company.address]=测试地址"
	curl -g "http://scm.laobao.com:9291/tbw_warehouses.json?s[like[tbc_company.address]]=1%25"
	curl -g "http://scm.laobao.com:9291/tbw_warehouses.json?s[date[tbc_company.created_at]]=2016-05-11"
	curl -g "http://scm.laobao.com:9291/tbw_warehouses.json?s[range[tbc_company.company_code]]=1,"
	curl -g "http://scm.laobao.com:9291/tbw_warehouses.json?s[in[tbc_company.company_code]]=11,12"


### 浏览接口

	curl http://localhost:3000/base_suppliers/1.json

### 新增接口

	curl  -d "base_supplier[fax]=1234&base_supplier[old_supplier_id]=456" http://localhost:3000/base_suppliers.json

### 修改接口

	curl  -X PUT -d "base_supplier[fax]=12" http://localhost:3000/base_suppliers/1.json


### 删除接口

	curl  -X DELETE http://localhost:3000/base_suppliers/4.json