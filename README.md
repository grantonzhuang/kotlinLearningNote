
## 扩展方法

如 判断一个字符串是否以英文字母开头

```kotlin
fun String.isEnglish(): Boolean {
    val firstChar = this[0].toInt()
    return (64 < firstChar && firstChar < 91) || (96 < firstChar && firstChar < 123)
}
```

## 字符串格式化

用
```kotlin
"varOneName is ${varOne}"
```

替代

```java
String.format("%s is ", varOne)
```

## lateinit

如果有需要稍后初始化的变量，可以使用 `lateinit` 关键字

```kotlin
lateinit var varLateInit: Object
```

## Parcelable

Android Studio 上已经有了 kotlin 的 Parcelable 生成插件了。

[Parcelable Code Generator(for kotlin)](https://plugins.jetbrains.com/plugin/8086)

## 类型推导

举一个例子，一个 ViewPager 中会展示好几个 fragment

```kotlin
class BaseFragment : Fragment()
class MusicsFragment : BaseFragment()
class ArtistsFragment : BaseFragment()
class AlbumsFragment : BaseFragment()
```

这几个 fragment 放在数组中

```kotlin
val pages: Array<Fragment> by lazy {
    arrayOf(MusicsFragment(), ArtistsFragment(), AlbumsFragment())
}
```

kotlin 会强制返回类型为 `Array<BaseFragment>`

假如只有一个 fragment 如

```kotlin
val pages: Array<BaseFragment> by lazy {
    arrayOf(MusicsFragment())
}
```

kotlin 会强制返回值的类型为 `Array<MusicsFragment>`。

也就是 kotlin 会让函数返回 **最精确的子类**。
