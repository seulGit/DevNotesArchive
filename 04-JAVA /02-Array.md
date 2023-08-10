### Arrays.sort()
- Arrays.sort() 메서드는 주어진 배열을 정렬하고 그 결과로 void를 반환합니다.
```
int[] arr = Arrays.sort(numbers);
// 리턴값 : void
```
- 배열을 정렬하려면 Arrays.sort() 메서드를 호출한 뒤에 따로 배열을 선언하거나 복사해야 합니다. 아래와 같이 수정할 수 있습니다.
```
int[] arr = Arrays.copyOf(numbers, numbers.length);
Arrays.sort(arr);
```
- 아래에서 arr 배열을 그대로 출력하려는 것은 배열 자체를 출력하는 것이 아니라 배열의 주소값을 출력하는 것이므로 의도한 결과가 나오지 않을 것입니다.
```
System.out.println(arr);
```
- 배열의 내용을 출력하려면 배열의 각 요소를 반복문을 통해 출력해야 합니다.
```
import java.util.Arrays;

class Solution {
    public int solution(int[] numbers) {
        int[] arr = Arrays.copyOf(numbers, numbers.length);
        Arrays.sort(arr);

        for (int num : arr) {
            System.out.println(num);
        }
        
        int answer = 0;
        return answer;
    }
}
```
