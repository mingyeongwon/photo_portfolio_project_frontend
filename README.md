# Minography - 사진 작가 포트폴리오 사이트
## 메인 페이지
![image](https://github.com/user-attachments/assets/458b704a-9fb5-44af-9fec-e9c7886fa839)
## 상세 페이지
![image](https://github.com/user-attachments/assets/42f0a757-1d96-4333-b14c-29156fda0144)
--
## 📚 관리자 페이지 접근 제어
프론트엔드에서는 Vue Router의 전역 네비게이션 가드를 사용하여, 로그인되지 않은 사용자가 관리자 페이지에 접근하는 것을 방지합니다.
```
 router.beforeEach((to, from, next) => {  
  // 'requiresAuth' 메타 필드가 설정된 경우, 관리자 인증이 필요합니다.  
  if (to.matched.some(record => record.meta.requiresAuth) && !store.state.id) {  
    next({  
      path: "/admin/login",            // 로그인 페이지로 리디렉션  
      query: { redirect: to.fullPath } // 로그인 후 원래 경로로 돌아가기 위한 쿼리 전달  
    });  
  } else {  
    // 인증된 상태이거나 인증이 필요 없는 경우, 그대로 이동  
    next();  
  }  
});
 ```
