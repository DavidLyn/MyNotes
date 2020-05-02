# 注解
## controller 注解

+ @PathVariable

> 获取 url 里面的参数
> 
> e.g  http://localhost:8080/user/123

```
@RequestMapping(value = "/user/{id}" ,method = RequestMethod.GET)
    public int hi(@PathVariable("id") int id){
        return  id;
}
```

+ @RequestParam

> 类似于 localhost:8080/hello?id=98&&name=wojiushimogui 这样的 url

```
@RestController
public class HelloController {
  //@RequestMapping(value="/hello",method= RequestMethod.GET)
  @GetMapping(value = "/hello")
  //required=false 表示url中可以不穿入id参数，此时就使用默认参数
  public String sayHello(@RequestParam(value="id",required =   false,defaultValue = "1") Integer id){
    return "id:"+id;
  }
}
```

