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
