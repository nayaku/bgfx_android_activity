# bgfx_android_activity

直接克隆下来就可以用。

因为太麻烦了，就没做子项目了。如果还有人用的话，以后再写个脚本自动写入对应文件。



# 常见错误

### *bgfx*-*android*-activity出现 'struct android_app *' with an rvalue of type 'void *'错误：

错误详细
```
In file included from E:\code\android\bgfx-android\bgfx\examples\common\entry\entry_android.cpp:26:
F:\Android\sdk\ndk-bundle\sources\android\native_app_glue\android_native_app_glue.c:238:25: error: cannot initialize a variable of type 'struct android_app *' with an rvalue of type 'void *'
```
其他地方也不知道怎么改。就直接修改`sdk\ndk-bundle\sources\android\native_app_glue\android_native_app_glue.c`的源代码了。

出错代码：

```cpp
struct android_app* android_app = calloc(1, sizeof(struct android_app));
```

修改为

```cpp
struct android_app* android_app = (struct android_app *)calloc(1, sizeof(struct android_app));
```