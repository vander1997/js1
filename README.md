# js1
在百度百科中添加可用的google、互动百科、维基搜索按钮。

fork了[sunforbeeing](https://greasyfork.org/zh-CN/users/20689-sunforbeeing)的项目，同时利用了[脚本代理](https://jsproxy.ga/)这个项目添加了稳定的google搜索和维护了维基搜索。

```
// ==UserScript==
// @name         在百度百科中添加可用的google、互动百科、维基搜索按钮
// @version      1.0
// @description  在百度百科中添加可用的google、互动百科、维基搜索按钮
// @match        *://baike.baidu.com/*
// @grant        none
// @author       vander1997
// @require      https://code.jquery.com/jquery-3.1.1.min.js
// ==/UserScript==

(function() {
	//搜索栏调整
	$('.header .layout').css('width', '95%');
	$('.wgt-searchbar-main').css('width', '100%');
	$('.search .form input').css('width', '400px');
	$('.search .form .help').remove();
	$('.wgt-userbar').css({'position':'static','float':'right'});
	//页面清理
	$('.new-side-share').remove();//分享
	$('.lemmaWgt-promotion-vbaike').remove(); //V百科
	$('.wgt-footer-main .content').remove();//页面底部
	$('.after-content').remove();//页面底部
     //添加google
	$('#searchForm #search').after('<button class="wiki" type="button" >google</button>');
	$('.wiki').click(function() {
			window.open("https://jsproxy.ga/-----https://www.google.com/search?source=hp&ei=em_eXIr5Ioyl8QWboZnIBw&q="+ $('#query').val()+"&gs_l=psy-ab.12..0l10.21325.22253..23022...0.0..0.236.639.0j1j2......0....1..gws-wiz.....0.MdvKdqtCwYA");
		});
	//添加互动百科
	$('#searchForm #search').after('<button class="hudong" type="button" >互动百科</button>');
	$('.hudong').click(function() {
			window.open("http://www.baike.com/wiki/" + $('#query').val());
		});
	//添加维基镜像词条
	$('#searchForm #search').after('<button class="wiki" type="button" >维基百科</button>');
	$('.wiki').click(function() {
			window.open("https://jsproxy.ga/-----https://zh.wikipedia.org/wiki/" + $('#query').val());
		});


})();
```
