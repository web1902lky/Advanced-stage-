    <script>
        "use strict"
        var eric={
            eid:1001,
            ename:"埃里克",
            salary:12000
        }
        //1.先定义一个隐姓埋名的半隐藏的属性，时间存储属性值
        Object.defineProperty(eric,"_eage",{
                value:25,//实际存储属性值
                writable: true,
                enumerable:false,//半隐藏
                configurble: false
        })
        // 定义报表用正式的属性名代替手保护的属性抛头露面
        Object.defineProperty(eric,"eage",{
            // 第一个保镖：帮用户去属性中取值
            get:function(){
               // console.log("自动调用get");
                return this._eage
            },
            // 第二个保镖：帮用户将新值送人属性中，单双会自动接到新值value
            set:function(valu){
               // console.log(`自动调用set方法，并自动传入${value}`);
               //先验证新值是否符合规定
                if(valu>=18&&valu<=65){
                    // 将新值放回手办胡的属性中
                    this._eage=valu;
                }else{//如果新值不符合规定，则不保存直接报错。
                    throw Error("年龄超范围！")
                }
            },
            enumerable:true,//代替受保护的属性抛头露面
            configurable:false//不能删除保镖
        })
        // 只要试图读取属性值时自动调用get方法
        console.log(eric.eage);
        // 只要试图修改属性值时
        eric.eage=26;//自动调用eage的set方法
        console.log(eric)
       // eric.eage=16
       // console.log(eric.eage)
    </script>
