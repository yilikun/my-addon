1. 创建`helloworld.cc`文件
```c++
    #include <node.h>

    using namespace v8;

    void HelloWorld(const FunctionCallbackInfo<Value>& args) {
        Isolate* isolate = args.GetIsolate();
        args.GetReturnValue().Set(String::NewFromUtf8(isolate, "hello world"));
    }

    void init(Local<Object> exports) {
        NODE_SET_METHOD(exports, "helloworld", HelloWorld);
    }

    NODE_MODULE(addon, init);
```
2. 创建`binding.gyp`文件
```
    {
      "targets": [
        {
          "target_name": "hellowold",
          "sources": [ "helloworld.cc" ]
        }
      ]
    }
```
3. 执行`node-gyp configure`

4. 执行`node-gyp build`
