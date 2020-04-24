完成了两个todo，运行得到的apk文件为register.apk, 代码如下所示：
# Chapter-5

 // todo 添加api  
    @FormUrlEncoded  
    @POST("user/register")  
    Call<UserResponse> register(@Field("username") String userName,  
    @Field("password") String password,  
    @Field("repassword") String repassword);  


// todo 做网络请求    
apiService.register(name, password, repassword).enqueue(new Callback<UserResponse>() {  
    @Override  
    public void onResponse(Call<UserResponse> call, Response<UserResponse> response) {  
        if (response.body() != null && response.body().user != null) {  
              Toast.makeText(RegisterActivity.this,  
              response.body().user.nickname + "注册成功",  
              Toast.LENGTH_SHORT).show();  
         }  
         else if (response.body() != null) {  
             Toast.makeText(RegisterActivity.this,  
                            "注册失败：" + response.body().errorMsg,  
                             Toast.LENGTH_SHORT).show();  
          }  
      }  
      @Override  
      public void onFailure(Call<UserResponse> call, Throwable t) {  
           Toast.makeText(RegisterActivity.this,  
                           "网络故障:" + t.getMessage(),  
       }  
});
