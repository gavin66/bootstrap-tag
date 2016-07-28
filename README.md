## 说明
这是一个 使用 jQuery 写的插件,用来生成标签.

## 特点
* 手动输入,下拉框选择两种方式生成标签
* 远程数据加载(支持 jQuery Ajax 加载)
* 彩色标签

## 依赖
* jQuery >= 1.7

## 文件
- [**dist/**](dist/js)
	- [tagger.min.js](dist/tagger.min.js) — 生产环境使用的 Javascript
	- [tagger-debug.js](dist/tagger-debug.js) —  用于调试
	- [tagger.min.css](dist/tagger.min.css) — 生产环境使用的 CSS
	- [tagger-debug.css](dist/tagger-debug.css) —  用于调试

## 使用
```html
<script src="jquery/dist/jquery.min.js"></script>
<script src="tagger.js"></script>
<script>
    jQuery(function($){
        $tag = $('#tag');
        $tag.tagger({
            color:'random',
            divide: true,
            tags:[],
            dropdown:{
//                items:['javascript','php','python','html5','nginx','redis','cache','laravel','thinkphp'],
                load: {
                    url: '/data.json',
                    type: 'GET',
                    dataType: 'json',
                    success: function(data){
                        return data;
                    }
                }
            }
        });
    });
</script>
```

## 配置
| 参数名 |  类型  | 默认值 | 可选值 | 描述 |
| -------- | ------- | --------- | -------- | ----- |
| color   | string | random | 'tagger-piece-LightPink', 'tagger-piece-conifer', 'tagger-piece-sauce', 'tagger-piece-RedGold', 'tagger-piece-ultramarine', 'tagger-piece-swarthy', 'tagger-piece-ink', 'tagger-piece-amber','random' | 标签的背景色: LightPink妃色, conifer松柏绿, sauce紫酱, RedGold赤金, ultramarine群青, swarthy黝黑, ink墨色, amber琥珀, random随机 |
| divide   | string / boolean | true |  | 输入框文字分隔字符 |
| tags | array | [] | | 初始化插件后显示的标签 |
| dropdown | object| false | 见下表 | 开启下拉框 |

| dropdown选项 |  类型  | 描述 |
| -------- | ------- | ----- |
| items | array  | 直接提供初始化数据 |
| load | object | 使用 ajax 远程获取初始化数据,见demo |

## 接口
```javascript
$tag = $('#tag');
$tag.tagger();
$tags = $tag.tagger('getTags'); // 获取当前已选取的 tags 数组
```
| Method  | 描述 |
| -------- | ----- |
| $tag.tagger('getTags') | 获取当前已选取的 tags 数组 | 
| $tag.tagger('addTag') | 触发添加按钮 | 

## 事件
```javascript
$tag = $('#tag');
$tag.tagger();
$tag.on('tagger.remove',function(){});
```
| 事件名  | 描述 |
| -------- | ----- |
| tagger.remove | 删除元素时触发 | 

## 贡献
如发现问题或者有好的提议请给我提交 Issues,谢谢!

## Github 项目地址
[tagger](https://github.com/gavin66/tagger)

