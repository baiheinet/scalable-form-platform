## 组件属性与API 
| 属性名 | 属性说明 | 属性类型 | 默认值 | 
| --- | --- | --- | --- | 
| locale |表单多语言配置| string | - | 
| defaultSubmitButtonComponent | 用于自定义默认提交按钮 | React Component | - | 
| widgets | 自定义基础字段集（对于每一个XForm自定义字段类型，都需要有相应的组件实现。必须实现的基础字段列表参见下面备注部分） | array | - | 
| fieldTemplate | 除Array、Object类型表单属性类型外的自定义字段模板（通过这个模板，决定XForm里面每一个表单字段的渲染模板），这个是react-jsonschema-form的特性，详见组件对应属性文档 | React Component | - | 
| arrayFieldTemplate | Array类型表单属性类型的自定义字段模板（通过这个模板，决定XForm里面每一个表单字段的渲染模板），这个是react-jsonschema-form的特性，详见组件对应属性文档 | React Component | - | 
| objectFieldTemplate | Object类型表单属性类型的自定义字段模板（通过这个模板，决定XForm里面每一个表单字段的渲染模板），这个是react-jsonschema-form的特性，详见组件对应属性文档 | React Component | - | 
| formContext | 在表单字段中能够读取到的上下文信息 | Object | {} | 
| formCode | 表单code | String | '' | 
| jsonSchema | react-jsonschema-form中的表单协议的一部分，用于表单渲染 | Object | {} | 
| uiSchema | react-jsonschema-form中的表单协议的一部分，用于表单渲染 | Object | {} | 
| formData | react-jsonschema-form中的表单协议的一部分，用于表单渲染 | Object | {} | 
| bizData | Scalable Form中扩展表单协议的一部分，用于表单渲染 | Object | {} | 
| className | 组件父容器指定class | string | '' |
