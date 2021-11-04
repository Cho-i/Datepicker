# Datepicker

jQuery에서 제공하는 달력 형식의 UI 위젯(widget)[^1] 중 하나이며, 날짜를 다룰 때 UI 형식으로 쉽게 날짜를 선택 하도록 도와주는 역할을 합니다. datepicker를 이용하면 많은 기능을 포함한 디자인된 달력을 간단한 코딩으로도 만들 수 있습니다. datepicker의 동작 순서는 먼저 datepicker 메소드를 토해서 jQuery가 javascript 해석기로 datepicker를 요청합니다. 요청을 받은 javascript 해석기는 DOM에서 id가 datepicker인 요소를 찾습니다. 다시 javascript 해석기로 return 후 화면으로 출력합니다.

![datepicker UML](/Users/chooomu/Sites/joy/datepicker/img01.png)

[^1]: 프로그래밍에서 widget은 작은 프로그램을 의미하며, 사용자와 컴퓨터가 상호 작용하는 인터페이스 요소.

## 사용방법

datepicker를 사용하기 위해서는 기본적으로 다음 3가지 File을 import해야 합니다.

```html
// jQuery UI CSS파일
<link rel="stylesheet" href="http://code.jquery.com/ui/1.8.18/themes/base/jquery-ui.css" type="text/css"/>
// jQuery 기본 js파일
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js"></script>
// jQuery UI 라이브러리 js파일
<script src="http://code/jquery.com/ui/1.8.18/jquery-ui.min.js"></script>
```

단, offline인 경우에는 위의 파일들을 직접 다운받아 해당 File의 경로를 설정해야 합니다.

datepicker의 가장 기본적인 코드를 살펴보면 다음과 같습니다.

```javascript
//script구문 내부에 해당 메소드를 입력합니다.
$(function() {
    $( "#testDatepicker" ).datepicker({
    });
});
```

위의 코드를 살펴보면 function 내부에 datepicker 선택자와 메소드로 이루어져 있습니다.

```html
//해당 메소드에서 선택자로 지명한 id가 testDatepicker인 input 태그를 추가합니다.
<input type="text" id="testDatepicker">
```

![datepicker](/Users/chooomu/Sites/joy/datepicker/img02.png)

datepicker를 출력할 input tag를 선언하면, 해당 id를 찾아 기본 옵션의 날짜선택기를 사용할 수 있습니다.

## 자주 사용하는 옵션

![option](/Users/chooomu/Sites/joy/datepicker/img03.png)

다양한 옵션들을 실제로 사용해 보면서 결과를 확인하면 다음과 같습니다.

```javascript
$(function() {
  $( "#testDatepicker" ).datepicker({
        showOn: "both", 
        buttonImage: "button.png", 
        buttonImageOnly: true 
  });
});
```

showOn 옵션은 button 과 image 의 표시여부를 결정하며, 둘 다 선택하거나 한가지만 선택할 수 있습니다. image를 선택할 경우에는 사용할 image의 경로를 정확하게 입력해야 제대로 화면에 나옵니다. buttonImageOnly 옵션은 image를 button 형식 또는 단순히 image만 표시하도록 설정할 수 있습니다. Test를 하기 위해 임의의 이미지를 선택한 모습입니다.

![img04](/Users/chooomu/Sites/joy/datepicker/img04.png)

달을 이동하는 옵션에 관한 설명은 다음과 같습니다.

```javascript
$(function() {
  $( "#testDatepicker" ).datepicker({
         changeMonth: true, 
         changeYear: true,
         nextText: '다음 달',
         prevText: '이전 달' 
  });
});
```

기본적으로 month이나 year를 이동하려면 상단좌우의 화살표 이미지를 클릭해서 한달 단위로 이동을 할 수 있습니다. 하지만 changeMonth와 changeYear 옵션을 통해서 select box 형식으로 한번에 원하는 month나 year를 선택할 수 있습니다. 또한 nextText와 prevText의 설정을 통해 상단 화살표 툴팁을 정할 수 있습니다.

![img05](/Users/chooomu/Sites/joy/datepicker/img05.png)

한번에 여러 month를 표현할 때는 다음과 같이 배열 형식으로 표현할 month의 개수를 설정할 수 있습니다.

```javascript
$(function() {
    $( "#testDatepicker" ).datepicker({
         numberOfMonths: [2,2]
  });
});
```

![img06](/Users/chooomu/Sites/joy/datepicker/img06.png)

날짜선택기의 하단메뉴 설정과 날짜 형식을 설정하는 방법에 대해서 소개하겠습니다.

```javascript
$(function() {
    $( "#testDatepicker" ).datepicker({
         showButtonPanel: true, 
         currentText: '오늘 날짜', 
         closeText: '닫기', 
         dateFormat: "yymmdd"
  });
});
```

하단메뉴에는 닫기와 현재날짜를 선택할 수 있으며 showButtonPanel을 통해 표시 여부를 결정하며, closeText와 currentText를 통해서 표시하는 Text를 설정 할 수 있습니다. 또한 dateFormat을 통해서 선택한 날짜에 대한 표현을 다양하게 설정할 수 있습니다.

![img07](/Users/chooomu/Sites/joy/datepicker/img07.png)

날짜선택기의 month와 week의 표현도 사용자가 설정할 수 있습니다.

```javascript
$(function() {
    $( "#testDatepicker" ).datepicker({
         changeMonth: true, 
         dayNames: ['월요일', '화요일', '수요일', '목요일', '금요일', '토요일', '일요일'],
         dayNamesMin: ['월', '화', '수', '목', '금', '토', '일'], 
         monthNamesShort: ['1','2','3','4','5','6','7','8','9','10','11','12'],
         monthNames: ['1월','2월','3월','4월','5월','6월','7월','8월','9월','10월','11월','12월']
  });
});
```

dayNamesMin은 날짜선택기에 표시하는 요일의 약자를 설정하며, dayNames 설정은 날짜선택기에서 해당 요일의 tooltip에 나타나는 Text를 설정하는 옵션입니다. 또한 monthNamesShort는 changeMonth 옵션이 true일 경우 표현하는 month의 Text를 설정하며, monthNames는 반대로 changeMonth 옵션이 false일 경우 표현하는 month의 Text를 설정할 수 있습니다.

![img08](/Users/chooomu/Sites/joy/datepicker/img08.png)

마지막으로 날짜 선택시 날짜의 선택범위를 설정하는 옵션입니다.

```javascript
$(function() {
    $( "#testDatepicker" ).datepicker({
         minDate: -20, 
         maxDate: "+3D"
  });
});
```

minDate는 설정할 최소 날짜를 의미하며 현재날짜를 기준으로 +-를 통해 일단위로 설정 할 수 있으며, 현재날짜에 대한 상대 날짜가 아닌 절대날짜로 D(날짜), M(달),Y(년)을 숫자 뒤에 붙여서 표현할 수 있습니다.

![img09](/Users/chooomu/Sites/joy/datepicker/img09.png)

## 사용한 예시

엠오더 : http://code.d2.co.kr/2020/madforgarlic/m_order/app/html/gift/gift_box.html

```javascript
$('#datepicker').datepicker({
			dateFormat: 'yy.mm.dd',
			prevText: '이전 달',
			nextText: '다음 달',
			monthNames: ['1','2','3','4','5','6','7','8','9','10','11','12'],
			monthNamesShort: ['1','2','3','4','5','6','7','8','9','10','11','12'],
			dayNames: ['일','월','화','수','목','금','토'],
			dayNamesShort: ['일','월','화','수','목','금','토'],
			dayNamesMin: ['일','월','화','수','목','금','토'],
			showMonthAfterYear: true,
			yearSuffix: '.',
			//오늘 날짜부터 선택 가능
			minDate:0
		});
```

폭스바겐쇼룸 : https://code.d2.co.kr/VW_showroom/responsive/html/apply/testdrive.html

```javascript
$('#datepicker').datepicker({
			dateFormat: 'yy.mm.dd',
			prevText: '이전 달',
			nextText: '다음 달',
			monthNames: ['1','2','3','4','5','6','7','8','9','10','11','12'],
			monthNamesShort: ['1','2','3','4','5','6','7','8','9','10','11','12'],
			dayNames: ['일','월','화','수','목','금','토'],
			dayNamesShort: ['일','월','화','수','목','금','토'],
			dayNamesMin: ['일','월','화','수','목','금','토'],
			showMonthAfterYear: true,
			yearSuffix: '.',
			beforeShow : function(input,inst){
				var offset = $(input).offset();
				var height = $(input).height();
				window.setTimeout(function () {
					$(inst.dpDiv).css({ top: (offset.top + height) + 'px', left:offset.left + 'px' })
				}, 1);
			}
		});
```

폭스바겐VDL : http://code.d2.co.kr/2021/VDL/app/html/calender/lead_calender.html

```javascript
// 화면단 보여주기 위해 임의 작업
var enableDays = ['2021.11.11', '2021.11.20', '2021.11.28', '2021.11.30'];
var dayrates = ['+4', '+1', '+10', '+10'];
function enableAllTheseDays(date) {
  var fDate = $.datepicker.formatDate('yy.mm.dd', date);
  var result = [true, ''];

  $.each(enableDays, function(k, d) {
    if (fDate === d) {
      //날짜선택여부, 날짜에 추가할 class, 이 날짜에 대한 툴팁
      result = [true, 'count', dayrates[k]];
    }
  });
  return result;
}
//달력
$('#datepicker').datepicker({
  dateFormat: 'yy.mm.dd',
  prevText: '이전 달',
  nextText: '다음 달',
  monthNames: ['1','2','3','4','5','6','7','8','9','10','11','12'],
  monthNamesShort: ['1','2','3','4','5','6','7','8','9','10','11','12'],
  showMonthAfterYear: true,
  yearSuffix: '.',
  beforeShowDay: enableAllTheseDays
});
```

```css
.ui-datepicker .ui-datepicker-calendar tbody tr td.count[title]:after {
    content: attr(title);
    display: block;
    position: absolute;
    top: 0;
    right: -5px;
    font-size: 10px;
    color: #00B0F0;
}
```

datepicker에서 제공하는 함수 beforeShowDay를 이용하여 툴팁(title)을 넣은 후, CSS 요소 속성값(텍스트)를 content에 넣는걸 활용해 작업 https://developer.mozilla.org/en-US/docs/Web/CSS/attr()



**참고**

- https://jqueryui.com/datepicker/
- https://api.jqueryui.com/datepicker/
- https://www.nextree.co.kr/p9887/

