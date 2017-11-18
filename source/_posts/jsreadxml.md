---
title: js读取本地文件
date: 2017-10-29 09:22:53
tags: js

toc: true

categories: 前端

author: shangrila-kun
---

​	以前，在写页面的时候，都采取了硬编码，这次接到一个需求，做一个展示界面，用来展示各个项目，并提供入口，需求是展示界面的项目内容主要展示的是:已上线项目、待上线项目、内网项目，由于项目的划分多变，所以，最好是能够通过配置来展示页面的内容，就考虑了js读取本地xml。

<!--more-->

# js读取xml

代码内容如下：

~~~js
function autoLoadConf() {
   
       /*读取配置文件*/
       
       $.ajax({
                    url: "../nav/conf/links.xml",
                    dataType: 'xml',
                    type: 'GET',
                    timeout: 2000,
                    error: function(xml)
                    {
                        alert("读取配置文件失败！");
                    },
                    success: function(xml)
                    {

                        var jqueryObject = $(xml);//把读取的xum对象转换为jquery对象
                        /*已上线项目*/
                        var onlineArray = readXml(jqueryObject,"websites","online_websites","online_website");
                        addLiContent($("#onlineLinkUl"),onlineArray);
                        /*待上线项目*/
                        var weiArray = readXml(jqueryObject,"websites","wei_websites","wei_website");
                        addLiContent($("#weiLinkUl"),weiArray);
                        /*内网正式项目项目*/
                        var neiArray = readXml(jqueryObject,"websites","nei_websites","nei_website");
                        addLiContent($("#neiLinkUl"),neiArray);

              
                    }  

                });
}

function readXml(jqueryObject,f1,f2,f3){
    var arrayObject = new Array();
    jqueryObject.find(f1).find(f2).find(f3).each(function(i){
    var online = new Object();
    online.title = $(this).find("title").text();
    online.link = $(this).find("link").text();
    arrayObject.push(online);
  });
  console.log(arrayObject);
  return arrayObject;
}

/*给指定的ul添加li的内容*/
/*备注：class='item s"+((i+1)%9+1)+"' ((i+1)%9+1)此代码的写法是经过测试发现，css样式只有是s1到s9类。  */
function addLiContent(ulObject,arrayObject){//参数一，获取指定ul的对象，参数二，获取读xml遍历出来的数组
    for(var i = 0;i<arrayObject.length;i++){
        var hrefValue = arrayObject[i].link;
        var titleValue = arrayObject[i].title;
        var liHtml="<li class='item s"+((i+1)%9+1)+"' id=\"btn-in1\">"+
          "<a href='"+hrefValue+"'  target='_blank'>"+
            "<p class=\"pic\"><span class=\"fa fa-database fa-5x\"></span></p>"+
            "<p class=\"name\">"+titleValue+"</p><p><button class='btn-in in1' style=\"color: rgb(255, 255, 255); background: transparent;\">进入</button></p>"+
        "</a></li>";
        ulObject.append(liHtml);
    }
}
~~~

