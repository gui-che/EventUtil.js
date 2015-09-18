# EventUtil.js

摘自Javascript高级程序设计 (第3版) p.360

---

为了以跨浏览器的方式处理事件，不少开发人员会使用能够隔离浏览器差异的Javascript库，还有一些开发人员会自己开发最适合的事件处理的方法。自己编写代码其实也不难，只要恰当地使用能力检测即可。要保证处理事件的代码能在大多数浏览器下一致地运行，只需关注冒泡阶段。

可以像下面这样使用EventUtil对象：

{% codeblock %}
    
    var btn = document.getElementById( 'myBtn' );

    var handler = function( event ) {
        var target;

        event = EventUtil.getEvent( event );
        EventUtil.preventDefault( event );
        EventUtil.stopPropagation( event ): 
        target = EventUtil.getTarget( event );

        if ( "innerText" in target ) {
            target.innerText = target.innerHTML + 'X';
        } else {
            target.textContent = target.textContent + 'X';
        }

    };

    EventUtil.addHandler( btn, 'click', handler );
    EventUtil.removeHandler( btn, 'click', handler );

{% endcodeblock %}
