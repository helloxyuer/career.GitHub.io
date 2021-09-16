```

const MyClass = class Me {
    //实例对象自身的属性都定义在类的头部
    age = '12'

    //一个类必须有constructor()方法，如果没有显式定义，一个空的constructor()方法会被默认添加。
    constructor(props) {
        //this为函数实例
        this.name = props.name
        
        //new.target会返回子类。利用这个特点，可以写出不能独立使用、必须继承后才能使用的类。
        if (new.target === MyClass) {
            throw new Error('本类不能实例化');
        }
        console.log(new.target === MyClass);//true
        //默认返回值即为实例可以修改
        // return Object.create(null);
    }
    //支持set和get重写 此处重写prop属性
    get prop() {
        return 'getter';
    }
    set prop(value) {
        console.log('setter: '+value);
    }
    //类的名字是Me，但是Me只在 Class 的内部可用，指代当前类
    getClassName() {
        return Me.name;
    }
    //静态属性 新提案
    static myStaticProp = 42;

    //静态方法,供类调用
    static bar() {
        //静态方法包含this关键字，这个this指的是类，而不是实例
        this.baz();
    }
    //父类的静态方法，可以被子类继承。
    static baz() {
        console.log('hello');
    }
    //静态方法可以与非静态方法重名
    baz() {
        console.log('world');
    }

    //私有属性(提案)
    #a;
    #b;
    get a() {
        return this.#a;
    }
    set a(value) {
        this.#a = +value;
    }

    #sum() {
        return this.#a + this.#b;
    }

    #xValue = 0;

    get #x() { return this.#xValue; }
    set #x(value) {
        this.#xValue = value;
    }


    static PI = 22 / 7;
    static #totallyRandomNumber = 4;

    static #computeRandomNumber() {
        return MyClass.#totallyRandomNumber;
    }

    static random() {
        console.log('I heard you like random numbers…')
        return MyClass.#computeRandomNumber();
    }
}
//静态属性
MyClass.prop = 1;

MyClass.bar() // 'hello'

MyClass.PI // 3.142857142857143
MyClass.random()
// I heard you like random numbers…
// 4
MyClass.#totallyRandomNumber // 报错
MyClass.#computeRandomNumber() // 报错


```
