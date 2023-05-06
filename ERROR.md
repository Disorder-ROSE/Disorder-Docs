# 1. android studio에서 virtual device가 안됨
해결하는데 참고했던 블로그: https://jeunna.tistory.com/139

요약: 컴퓨터 전원켤때 esc와 delete키 연타해서 BIOS들어가서 가상화 설정 바꿈 
# 2. android studio에서 run버튼 안보임
해결: https://velog.io/@fltk1004/android-studio-run%EB%B2%84%ED%8A%BC-%EC%95%88%EB%B3%B4%EC%9E%84-chromeweb%EC%95%88%EB%B3%B4%EC%9E%84

요약: flutter sdk경로 잘 설정하기
# 3. 집 데스크탑에선 되는데 노트북에선 해결되지 않는 문제
- virtual device
- firebase 연동

# 4. android studio virtual device에서 영어만 가능
에러라기보다는 의문점
TextField안에 게시판의 제목,아이디,내용을 적을때 영어만 나타남
한국어로 바꿀 수는 없나?

# 5. AttributeError: 'NoneType' object has no attribute 'shape' 에러발생
 데이터셋을 AI hub에서 구해와 yolov5를 돌리다가 결과가 부정확해서
 데이터 증식(generator)을 위해 shift range코드 작성중
 제목과 같은 에러가 발생하였다.
 images폴더 안의 이미지파일과 labels폴더 안의 텍스트파일 둘 다 고치는 코드를 작성하다보니
 경로문제라고 생각하여 확인해보았지만 경로는 정확하였다.
 구글링결과 (참고블로그: https://suy379.tistory.com/75)
 경로에 한글이 들어가있어도 이와같은 에러가 뜬다고 하여 한글을 모두 숫자로 바꿔주었더니 에러가 해결되었다.
