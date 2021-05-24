## 组件属性与API 

| 属性名 | 属性说明 | 属性类型 | 默认值 | 
| --- | --- | --- | --- | 
| width | 设置组件容器的宽度，为保证正常展示，最小宽度为1000px| number | 'auto' | 
| height | 设置组件容器的高度 | number | 'auto' | 
| platformConfigSupport | 设置是否支持适配端切换，如果设置为true，则顶部工具栏中才会有适配端切换入口。对于新建的表单，默认为PC端；对于编辑的表单，会依据上次保存编辑时的适配端来显示 | boolean | false | 
| platform | 设置组件支持的适配端，如果设置了该属性，默认全部表单都会采用该适配端 | laptop(PC端)、mobile（手机端）、both（两者） | - | 
| locale | 指定组件的多语言，其值为标准的[语言]和[国家]中间用中划线分隔（例如en-us），默认值为浏览器设置的语言，如果传入不能识别的值或自动启用英文 | navigator.language.toLocaleLowerCase() | |
| emptyPlaceholder | 自定义组件空状态时的占位符，适用于有统一空状态占位设计的场景，使组件设计风格统一 | React Component | 有默认占位符 | 
| popupContainer | 指定组件中modal、popup组件渲染的DOM节点，默认为document.body | function | () => document.body | 
| onImagePreview | 当用户点击表单中图片时触发，该属性接受一个方法，该方法中会注入点击图片的url地址，可以用来做自定义的图片预览处理。默认为打开新的浏览器窗口来预览图片 | function | function(url) {window.open(url);} | 
| defaultActionButtons | 配置是否使用内置的动作按钮，内置的动作按钮为“保存”操作，位置在表单设计器的右下角，允许设置该属性为false来使用自定义的动作按钮 | Boolean | true | 
| renderActionButtons | 自定义渲染动作按钮，该属性为一个返回待渲染动作按钮的React Element | function(saveAction)，方法中会传入可以直接调用【保存】操作逻辑，与`handleFormSave`相同 | - | 
| namespace | 改属性定义了store中的namespace，主要用来防止多个组件实例导致的store数据共享问题。强烈建议设置改属性并要保证值的唯一性 | String | xformBuilderDefault | 
| systemFieldSupport | 是否开启对表单模板字段功能的支持 | Boolean | false | 
| commonFieldSupport | 是否开启对通用字段功能的支持 | Boolean | false | 
| bizDataSupport | 是否开启对字段业务属性的支持 | Boolean | false | 
| supportLangList | 在组件支持的多语言中只开启对指定列表中的多语言类型的表单配置，如果不配置该属性，则默认内置多语言都支持（该属性只有在langConfigSupport属性设置为true时才生效，默认启用的语言类型的规则为：如果设置的locale属性值在supportLangList列表中，则默认启用语言与设置的组件语言相同，否则启用设置的supportLangList列表中的第一个语言） | Array | - | 
| supportFieldList | 在组件内置的自定义字段中只开启对指定列表中的自定义字段的配置的支持，如果不配置该属性，则默认内置自定义字段都支持配置（该属性值为内置自定义字段的code值的数组，内置的自定义字段以及code值见下面的说明） | Array | [] | 
| supportConfigList | 在组件内置的字段配置项中只开启对指定列表中的字段的配置的支持，如果不配置该属性，则默认内置字段配置项都支持配置（该属性值为内置字段配置项的code值的数组，内置的字段配置项code值见下面的说明） | Array | ['code', 'placeholder', 'description', 'value', 'dataSource', 'validate', 'server', 'require', 'hidden'] | 
| getInstance | 通过该属性，能够获取到组件暴露出来的一些API，详见下面的具体API说明 | Function | - | 
| beforeSubmit | 在XFormBuilder提交编辑前执行，在提交前可以做一些校验；return false;可以组织XFormBuilder提交 | Function | `function(Object schema{jsonSchema, uiSchema, formData, bizData, sequence}) {return true;}` | 
| onError | 异常处理属性，会上报组件componentDidCatch中捕获到的错误 | function(error, info) | - | 
| onSubmit | 允许在提交编辑之后执行一些自定义逻辑，该属性的方法中会注入此次提交生成的formCode值 | Function | `function(formCode, Object schema{jsonSchema, uiSchema, formData, bizData, sequence}) {}` | 
| registerWidgets | 允许通过该属性注册可以配置的自定义表单字段 | array | [] |

registerWidgets为高级用法，该属性的值为一类特定格式的Object组成的数组，表示可以注册多种不同的组件配置。

可以通过组件的getInstance属性来获取到组件暴露的一些API：

handleFormPreview(): 调用该方法会直接弹出表单设计器的【预览】模态框。适用于自定义预览按钮的使用场景（2.0.0版本以上，预览会集中在顶部工具栏，不再支持自定义预览）
handleFormSave(): 调用该方法会直接执行表单设计器的【保存】逻辑，表单数据会自动保存或更新。适用于自定义预览按钮的使用场景




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
