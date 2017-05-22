
## 每日反馈脚本

```javascript
/**
 * 每日反馈 自动填写并提交
 * @param  {[type]} name       [姓名]
 * @param  {[type]} alpha      [每道题的选项]
 * @param  {[type]} suggestion [评论 提出问题]
 * @return {[type]}            [无]
 */
function feedBack(name,alpha,suggestion){
	var form=document.querySelector('form'),
		ol=document.querySelector('#targets'),
		lis=[].slice.apply(ol.children),
		index=0;
	switch(alpha){
		case 'a': index=0;break;
		case 'b': index=1;break;
		case 'c': index=2;break;
		case 'd': index=3;break;
		default:;
	}
	name && (form.children[0].children[0].children[1].value=name);
	alpha && lis.forEach(item=>item.children[1].children[index].children[0].setAttribute('checked',true));
	suggestion && (form.children[4].value=suggestion);

    var event = document.createEvent("MouseEvents");
    event.initMouseEvent("click", true, true, document.defaultView, 0, 0, 0, 0, 0,false, false, false, false, 0, null);
    var btn=document.querySelector('#btn');

    setTimeout(function(){
        btn.dispatchEvent(event);
    },100);
}

feedBack('郭亮','a','');
```