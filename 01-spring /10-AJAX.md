AJAX
====

키값은 컬럼명,
url은 컨트롤러 value랑 맞춰준다.
- datatype은 받아올 타입
- contentType은 보낼 타입
- 보라색data 는 보낼데이타
- 흰색data는 ajax통신이 된 결과값

객체 만들고 컨트롤러에서 value 맞춰서 생성하기


success: function()부분 (data, status, xhr어쩌고)는 자리가 정해져있다

```
$(function() {
   $('.section_footer_commentList_viewMore_btn').click(function() {
      let view_more = {
            camping_id : camping_id,
            s_count : s_count,
      };
      $.ajax({
         type : "POST",
         url : "/community/joinNotice/view_more",
         dataType : "text",
         contentType : "application/json",
         data : JSON.stringify(view_more),
         success : function(data) {
            $('.section_footer_commentList').append(data);
         },
         error : function(data) {
            console.log(data);
         }
      });
      s_count = s_count+5;
      if(s_count>reply_count || s_count==reply_count){
         document.querySelector(".section_footer_commentList_viewMore").style.display = "none";
      }
   })
})
```
<br/>

```
let detail_name = document.querySelector('#detail_name');
let detail_gender_m = document.querySelector('#detail_gender_m');
let detail_gender_f = document.querySelector('#detail_gender_f');
let detail_department = document.querySelector('#detail_department');
let detail_num = document.querySelector('#detail_num');
let detail_joindate = document.querySelector('#detail_joindate');
let detail_phonenum = document.querySelector('#detail_phonenum');
let detail_email = document.querySelector('#detail_email');
let detail_address_one = document.querySelector('#detail_address_one');

$(function() {
    $('.xi-search').click(function() {
        let search_name = document.querySelector("#search_name").value;
        let search_department = document.querySelector("#search_department").value;
        let search_num = document.querySelector("#search_num").value;
        let search_joindate = document.querySelector("#search_joindate").value;
        let search_phone = document.querySelector("#search_phone").value;
        let search_mail = document.querySelector("#search_mail").value;
        // console.log(search_name);
        // console.log(search_department);
        // console.log(search_num);
        // console.log(search_joindate);
        // console.log(search_phone);
        // console.log(search_mail);


        //검색 부분
        let search_details = {
            emp_name : search_name,
            dept_name: search_department,
            emp_num : search_num,
            join_date : search_joindate,
            emp_phonenum : search_phone,
            emp_email : search_mail
        };

        $.ajax({
            type : "POST",
            url : "/admin/admin_personnelCard/search",
            dataType : "text",
            contentType : "application/json",
            data : JSON.stringify(search_details),
            success : function(data) {
                $('.result_table').html(data);

                let search_list_contents = document.querySelectorAll('.search_list_contents');

                for(let i=0; i<search_list_contents.length; i++){
                    search_list_contents[i].addEventListener('click', function (){
                        //이름
                        detail_name.value = this.children[0].textContent;
                        //성별
                        if (this.children[1].textContent == 'male'){
                            detail_gender_m.selected=true;
                        } else {
                            detail_gender_f.selected=true;
                        }
                        //
                        detail_department.value = this.children[2].textContent;
                        detail_num.value = this.children[3].textContent;
                        detail_joindate.value = this.children[4].textContent;
                        detail_phonenum.value = this.children[5].textContent;
                        detail_email.value = this.children[6].textContent;
                        detail_address_one.value = this.children[7].value;
                    })
                }
            },
            error : function(data) {
                alert("오류가 발생했습니다. 페이지를 새로고침해주세요")
            }
        });
    })
})
```


```
$.ajax({
	url: "url명" // 요청이 전송될 URL(컨트롤러)
	type: "POST" // http 요청방식(기본값은 get)
	async: true // 요청시 동기/비동기 전송방식 설정(T: 비동기 / F: 동기) 기본값은 TRUE
	cache: true // 캐시 사용 여부
	timeout: 3000 // 요청 제한 시간 안에 완료되지 않으면 요청취소 or 에러 콜백 호출
	data: // 요청시에 포함될 데이터
	processData: // 데이터를 아래의 컨텐츠 타입 프로퍼티에 맞게 변환했는지 확인
	contentType: "application/json" //응답데이터 형식(명시하지않으면 자동으로 추측)
	dataType: "json" // 응답의 데이터 형식
	beforeSend: function(){
		//요청전 호출되는 함수
	},
	success: function(data, status, xhr){
		//요청에 대해 정상적으로 응답받았을 경우 호출되는 콜백함수 
		data: 응답 결과 데이터 
		status: 응답 결과 코드(200)
		xhr: xmlhttprequest 헤더 데이터 
	},
	error: function(xhr, status, error){
		// 응답을 받지 못했거나 정상적인 응답이지만 데이터 형식이 확인이 안된다면
		// 호출되는 콜백함수
		// ex: 데이터 타입을 지정해서 응답받을 형식을 지정했지만
		// was에서는 엉뚱한 데이터로 응답하면 error가 호출 
	},
	complete: function(xhr, status) {
		// success가 호출되었건, error가 호출되었건 콜백 호출 후
		// 반드시 호출하는 콜백함수 
	}
});
```
