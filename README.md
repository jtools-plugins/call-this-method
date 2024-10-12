# call-this-method
- 1. 支持调用spring容器中的任意方法,包括接口和抽象类,以及抽象泛型方法
- 2. 支持调用任意静态方法
- 3. 支持通过groovy脚本执行代码,包括不限于在spring容器以及离线模式执行,提供log.debug(msg),log.info(msg),log.warn(msg),log.error(msg)向jtools中输出打印日志
- 4. 执行任意方法之前之后提供脚本,可直接修改请求参数,类型,响应结果等等,前置脚本类型包含: 全局脚本,项目脚本,模块脚本,函数脚本,后置脚本包含: 全局脚本,项目脚本,模块脚本,后置脚本
- 5. 每次调用将会保存历史记录,可在历史记录查看调用代码,脚本,响应结果等等,并且可从历史记录恢复到调用栈进行调用

# 脚本说明
```markdown
ctx.attributes: Map<String,Object> 脚本上下文缓存数据,前置脚本后置脚本都可以访问,同一个对象,使用场景,例如: 打印方法执行时长
ctx.parameterMap: Map<String,Object> key: 参数名 value: 参数值,可在前置脚本中覆盖对应的参数
ctx.parameterTypes: Map<String,Class<?>> key: 参数名 value: 参数类型,可在前置脚本中修改对应参数名的参数类型,会影响获取的方法
ctx.conversionService:org.springframework.core.convert.ConversionService
ctx.context: org.springframework.context.ApplicationContext
ctx.env: org.springframework.core.env.Environment
ctx.classname: 反射调用的实例类型,前置脚本修改会影响调用实例
ctx.methodName 反射调用的方法,前置脚本修改会影响调用方法
ctx.error 后置脚本可获取,如执行出现异常,此参数可以获得异常
ctx.result 后置脚本可获取,此参数为方法执行结果,修改后会影响返回结果,如解密场景,可在后置脚本对结果解密,返回正确内容
```
# 使用方式参考
[博客](https://blog.csdn.net/qq_42413011/article/details/142438452)
