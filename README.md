# spring-security
springboot3 security



## 测试



1. 直接访问/controller/method 会返回[403](https://so.csdn.net/so/search?q=403&spm=1001.2101.3001.7020)状态
2. 访问一下/api/auth/login授权登后，再访问/controller/method才能看到数据





## 抄的

@see https://blog.csdn.net/yry0304/article/details/128276473

总结：在研究过程的时候遇到了哪些坑
以下内容供有经验的人阅读

1、authorizeRequests方法已废弃，取而代之的是authorizeHttpRequests。
2、@PermitAll注解是不好使的。
3、SecurityContextHolder.getContext().getAuthentication().isAuthenticated()永远都是true，所以即使是当前用户是anonymousUser时，也不能用来判断登录状态，必须要判断是否是AnonymousAuthenticationToken类型。
4、并不是所有的字符串都可以充当权限字符串，建议使用英文字母、冒号。
5、ROLE_开头的权限字符串代表角色，用错会导致无法判断权限。
6、SecurityContext在设置Authentication的时候并不会自动写入Session，读的时候却会根据Session判断，所以需要手动写入一次，否则下一次刷新时SecurityContext是新创建的实例。
7、HttpServletRequest已经从javax包移动到了jakarta包，是因为Spring Framework 6.0从Java EE升级到了Jakarta EE。

所以综上所述，大多数已知的第三方工具类和辅助框架已经失效，要么重新造轮子，要么开源开发者升级一下已有的项目。
