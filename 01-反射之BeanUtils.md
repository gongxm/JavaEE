# 01.下载

## Apache Commons BeanUtils 1.9.4

### Binaries

| [commons-beanutils-1.9.4-bin.tar.gz](http://mirrors.tuna.tsinghua.edu.cn/apache//commons/beanutils/binaries/commons-beanutils-1.9.4-bin.tar.gz) | [sha256](https://www.apache.org/dist/commons/beanutils/binaries/commons-beanutils-1.9.4-bin.tar.gz.sha256) | [pgp](https://www.apache.org/dist/commons/beanutils/binaries/commons-beanutils-1.9.4-bin.tar.gz.asc) |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| [commons-beanutils-1.9.4-bin.zip](http://mirrors.tuna.tsinghua.edu.cn/apache//commons/beanutils/binaries/commons-beanutils-1.9.4-bin.zip) | [sha256](https://www.apache.org/dist/commons/beanutils/binaries/commons-beanutils-1.9.4-bin.zip.sha256) | [pgp](https://www.apache.org/dist/commons/beanutils/binaries/commons-beanutils-1.9.4-bin.zip.asc) |

### Source

| [commons-beanutils-1.9.4-src.tar.gz](http://mirrors.tuna.tsinghua.edu.cn/apache//commons/beanutils/source/commons-beanutils-1.9.4-src.tar.gz) | [sha256](https://www.apache.org/dist/commons/beanutils/source/commons-beanutils-1.9.4-src.tar.gz.sha256) | [pgp](https://www.apache.org/dist/commons/beanutils/source/commons-beanutils-1.9.4-src.tar.gz.asc) |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| [commons-beanutils-1.9.4-src.zip](http://mirrors.tuna.tsinghua.edu.cn/apache//commons/beanutils/source/commons-beanutils-1.9.4-src.zip) | [sha256](https://www.apache.org/dist/commons/beanutils/source/commons-beanutils-1.9.4-src.zip.sha256) | [pgp](https://www.apache.org/dist/commons/beanutils/source/commons-beanutils-1.9.4-src.zip.asc) |



# 02.基本用法

```java
//给任意对象中的属性赋值
public static void setProperty(Object bean,String name,Object value)

//获取任意对象中的属性值
public static String getProperty(Object bean,String name)

//给任意对象中的属性批量赋值
public static void populate(Object bean,Map properties)

```

# 03.注意事项

BeanUtils工具类操作对象中的属性, 该属性必须有对应的**set/get方法**

populate方法中的Map对象, key是属性名, value是属性值, 如果Map对象中还有其他数据, 会自动跳过, 不会异常