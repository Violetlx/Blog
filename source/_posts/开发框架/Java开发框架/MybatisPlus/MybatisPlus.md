---
title: MybatisPlus
tags:
  - MybatisPlus
categories:
  - [开发框架]
  - [SpringCloud]
series: SpringCloud
description: MybatisPlus学习
top_img: >-
  	https://www.mulei.ltd/wp-content/uploads/2021/07/cover-mybatis-plus.png
cover: >-
  	https://www.mulei.ltd/wp-content/uploads/2021/07/cover-mybatis-plus.png
abbrlink: 8af9e237
date: 2024-09-09 17:39:20
---

# MybatisPlus简介

在日常开发生活中，单表的 **CRUD** 功能代码重复度很高，也没什么难度，但是这部分代码的开发量往往却比较大，开发起来相当费时。

因此，目前企业中会使用一些组件来简化 **CRUD** 开发工作，而国内，使用最多的一个组件就是 **MybatisPlus** 。



官方网站如下：

[![https://baomidou.com](images/frameworks/Java/mybatisplus/a/v1.png)](https://baomidou.com/)

**MybatisPlus** 不仅仅可以简化单表操作，而且还对 **Mybatis** 进行了增强。可以让我们能够简单高效地进行开发。

我们需要掌握的内容如下：

- 能利用 **MybatisPlus** 实现基本的 **CRUD**

- 使用条件构造器构建查询和更新语句

- 掌握 **MybatisPlus** 中常用的注解

- 会使用 **MybatisPlus** 处理枚举类、**JSON** 类型字段

- 会使用 **MybatisPlus** 实现分页

  

------



# 快速入门

创建一个 **MybatisPlus** 项目，并准备一些基础数据。

![MybatisPlus项目](images/frameworks/Java/mybatisplus/a/v2.png)



## Ⅰ环境准备

① 打开 **IDEA** 导入 **MybatisPlus** 项目

② 打开 **navicat** 导入 **mp.sql** 文件

![配置数据库](images/frameworks/Java/mybatisplus/a/v4.png)

③ 配置项目 **JDK** 版本

![配置jdk](images/frameworks/Java/mybatisplus/a/v3.png)

④ 在 **application.yml** 文件中配置参数

```YAML
spring:
  datasource:
    url: jdbc:mysql://127.0.0.1:3306/mp?useUnicode=true&characterEncoding=UTF-8&autoReconnect=true&serverTimezone=Asia/Shanghai
    driver-class-name: com.mysql.cj.jdbc.Driver
    username: root
    password: 123456
logging:
  level:
    com.itheima: debug
  pattern:
    dateformat: HH:mm:ss
```



## Ⅱ 快速开始

- 引入 **MybatisPlus** 依赖
- 定义 **Mapper**

### ① 引入依赖

**MybatisPlus **提供了 **starter**，实现了自动 **Mybatis** 以及 **MybatisPlus** 的自动装配功能，坐标如下：

```XML
<!--mybatis-plus-boot-starter-->
<dependency>
    <groupId>com.baomidou</groupId>
    <artifactId>mybatis-plus-boot-starter</artifactId>
    <version>3.5.3.1</version>
</dependency>
```

该依赖包含了对 **mybatis** 的自动装配，因此不需要 **Mybatis** 的 **starter** 。

```XML
<dependencies>
    <!--mybatis-plus-boot-starter-->
    <dependency>
        <groupId>com.baomidou</groupId>
        <artifactId>mybatis-plus-boot-starter</artifactId>
        <version>3.5.3.1</version>
    </dependency>
    <!--数据库连接-->
    <dependency>
        <groupId>com.mysql</groupId>
        <artifactId>mysql-connector-j</artifactId>
        <scope>runtime</scope>
    </dependency>
    <!--lombok-->
    <dependency>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
        <optional>true</optional>
    </dependency>
    <!--测试-->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
    </dependency>
</dependencies>
```

### ② 定义 Mapper

为了简化单表 **CRUD** 开发，**MybatisPlus** 已经提供了一个基础的 **BaseMapper** 接口来实现单表 **CRUD**

```java
/**
 * Mapper 继承该接口后，无需编写 mapper.xml 文件，即可获得CRUD功能
 * <p>这个 Mapper 支持 id 泛型</p>
 *
 * @author hubin
 * @since 2016-01-23
 */
public interface BaseMapper<T> extends Mapper<T> {

    /**
     * 插入一条记录
     *
     * @param entity 实体对象
     */
    int insert(T entity);

    /**
     * 根据 ID 删除
     *
     * @param id 主键ID
     */
    int deleteById(Serializable id);

    /**
     * 根据实体(ID)删除
     *
     * @param entity 实体对象
     * @since 3.4.4
     */
    int deleteById(T entity);

    /**
     * 根据 columnMap 条件，删除记录
     *
     * @param columnMap 表字段 map 对象
     */
    default int deleteByMap(Map<String, Object> columnMap) {
        return this.delete(Wrappers.<T>query().allEq(columnMap));
    }

    /**
     * 根据 entity 条件，删除记录
     *
     * @param queryWrapper 实体对象封装操作类（可以为 null,里面的 entity 用于生成 where 语句）
     */
    int delete(@Param(Constants.WRAPPER) Wrapper<T> queryWrapper);

    /**
     * 删除（根据ID或实体 批量删除）
     *
     * @param idList 主键ID列表或实体列表(不能为 null 以及 empty)
     */
    int deleteBatchIds(@Param(Constants.COLL) Collection<?> idList);

    /**
     * 根据 ID 修改
     *
     * @param entity 实体对象
     */
    int updateById(@Param(Constants.ENTITY) T entity);

    /**
     * 根据 whereEntity 条件，更新记录
     *
     * @param entity        实体对象 (set 条件值,可以为 null)
     * @param updateWrapper 实体对象封装操作类（可以为 null,里面的 entity 用于生成 where 语句）
     */
    int update(@Param(Constants.ENTITY) T entity, @Param(Constants.WRAPPER) Wrapper<T> updateWrapper);

    /**
     * 根据 Wrapper 更新记录
     *
     * @param updateWrapper {@link UpdateWrapper} or {@link LambdaUpdateWrapper}
     * @since 3.5.4
     */
    default int update(@Param(Constants.WRAPPER) Wrapper<T> updateWrapper) {
        return update(null, updateWrapper);
    }

    /**
     * 根据 ID 查询
     *
     * @param id 主键ID
     */
    T selectById(Serializable id);

    /**
     * 查询（根据ID 批量查询）
     *
     * @param idList 主键ID列表(不能为 null 以及 empty)
     */
    List<T> selectBatchIds(@Param(Constants.COLL) Collection<? extends Serializable> idList);

    /**
     * 查询（根据ID 批量查询）
     *
     * @param idList        idList 主键ID列表(不能为 null 以及 empty)
     * @param resultHandler resultHandler 结果处理器 {@link ResultHandler}
     * @since 3.5.4
     */
    void selectBatchIds(@Param(Constants.COLL) Collection<? extends Serializable> idList, ResultHandler<T> resultHandler);

    /**
     * 查询（根据 columnMap 条件）
     *
     * @param columnMap 表字段 map 对象
     */
    default List<T> selectByMap(Map<String, Object> columnMap) {
        return this.selectList(Wrappers.<T>query().allEq(columnMap));
    }

    /**
     * 查询（根据 columnMap 条件）
     *
     * @param columnMap     表字段 map 对象
     * @param resultHandler resultHandler 结果处理器 {@link ResultHandler}
     * @since 3.5.4
     */
    default void selectByMap(Map<String, Object> columnMap, ResultHandler<T> resultHandler) {
        this.selectList(Wrappers.<T>query().allEq(columnMap), resultHandler);
    }

    /**
     * 根据 entity 条件，查询一条记录
     * <p>查询一条记录，例如 qw.last("limit 1") 限制取一条记录, 注意：多条数据会报异常</p>
     *
     * @param queryWrapper 实体对象封装操作类（可以为 null）
     */
    default T selectOne(@Param(Constants.WRAPPER) Wrapper<T> queryWrapper) {
        return this.selectOne(queryWrapper, true);
    }

    /**
     * 根据 entity 条件，查询一条记录，现在会根据{@code throwEx}参数判断是否抛出异常，如果为false就直接返回一条数据
     * <p>查询一条记录，例如 qw.last("limit 1") 限制取一条记录, 注意：多条数据会报异常</p>
     *
     * @param queryWrapper 实体对象封装操作类（可以为 null）
     * @param throwEx      boolean 参数，为true如果存在多个结果直接抛出异常
     */
    default T selectOne(@Param(Constants.WRAPPER) Wrapper<T> queryWrapper, boolean throwEx) {
        List<T> list = this.selectList(queryWrapper);
        int size = list.size();
        if (size == 1) {
            return list.get(0);
        } else if (size > 1) {
            if (throwEx) {
                throw new TooManyResultsException("Expected one result (or null) to be returned by selectOne(), but found: " + size);
            }
            return list.get(0);
        }
        return null;
    }

    /**
     * 根据 Wrapper 条件，判断是否存在记录
     *
     * @param queryWrapper 实体对象封装操作类
     * @return 是否存在记录
     */
    default boolean exists(Wrapper<T> queryWrapper) {
        Long count = this.selectCount(queryWrapper);
        return null != count && count > 0;
    }

    /**
     * 根据 Wrapper 条件，查询总记录数
     *
     * @param queryWrapper 实体对象封装操作类（可以为 null）
     */
    Long selectCount(@Param(Constants.WRAPPER) Wrapper<T> queryWrapper);

    /**
     * 根据 entity 条件，查询全部记录
     *
     * @param queryWrapper 实体对象封装操作类（可以为 null）
     */
    List<T> selectList(@Param(Constants.WRAPPER) Wrapper<T> queryWrapper);

    /**
     * 根据 entity 条件，查询全部记录
     *
     * @param queryWrapper  实体对象封装操作类（可以为 null）
     * @param resultHandler 结果处理器 {@link ResultHandler}
     * @since 3.5.4
     */
    void selectList(@Param(Constants.WRAPPER) Wrapper<T> queryWrapper, ResultHandler<T> resultHandler);

    /**
     * 根据 entity 条件，查询全部记录（并翻页）
     *
     * @param page         分页查询条件
     * @param queryWrapper 实体对象封装操作类（可以为 null）
     * @since 3.5.3.2
     */
    List<T> selectList(IPage<T> page, @Param(Constants.WRAPPER) Wrapper<T> queryWrapper);

    /**
     * 根据 entity 条件，查询全部记录（并翻页）
     * @param page          分页查询条件
     * @param queryWrapper  实体对象封装操作类（可以为 null）
     * @param resultHandler 结果处理器 {@link ResultHandler}
     * @since 3.5.4
     */
    void selectList(IPage<T> page, @Param(Constants.WRAPPER) Wrapper<T> queryWrapper, ResultHandler<T> resultHandler);


    /**
     * 根据 Wrapper 条件，查询全部记录
     *
     * @param queryWrapper 实体对象封装操作类
     */
    List<Map<String, Object>> selectMaps(@Param(Constants.WRAPPER) Wrapper<T> queryWrapper);

    /**
     * 根据 Wrapper 条件，查询全部记录
     *
     * @param queryWrapper  实体对象封装操作类
     * @param resultHandler 结果处理器 {@link ResultHandler}
     * @since 3.5.4
     */
    void selectMaps(@Param(Constants.WRAPPER) Wrapper<T> queryWrapper, ResultHandler<Map<String, Object>> resultHandler);

    /**
     * 根据 Wrapper 条件，查询全部记录（并翻页）
     *
     * @param page         分页查询条件
     * @param queryWrapper 实体对象封装操作类
     * @since 3.5.3.2
     */
    List<Map<String, Object>> selectMaps(IPage<? extends Map<String, Object>> page, @Param(Constants.WRAPPER) Wrapper<T> queryWrapper);

    /**
     * 根据 Wrapper 条件，查询全部记录（并翻页）
     *
     * @param page          分页查询条件
     * @param queryWrapper  实体对象封装操作类
     * @param resultHandler 结果处理器 {@link ResultHandler}
     * @since 3.5.4
     */
    void selectMaps(IPage<? extends Map<String, Object>> page, @Param(Constants.WRAPPER) Wrapper<T> queryWrapper, ResultHandler<Map<String, Object>> resultHandler);

    /**
     * 根据 Wrapper 条件，查询全部记录
     * <p>注意： 只返回第一个字段的值</p>
     *
     * @param queryWrapper 实体对象封装操作类（可以为 null）
     */
    <E> List<E> selectObjs(@Param(Constants.WRAPPER) Wrapper<T> queryWrapper);

    /**
     * 根据 Wrapper 条件，查询全部记录
     * <p>注意： 只返回第一个字段的值</p>
     *
     * @param queryWrapper  实体对象封装操作类（可以为 null）
     * @param resultHandler 结果处理器 {@link ResultHandler}
     * @since 3.5.4
     */
    <E> void selectObjs(@Param(Constants.WRAPPER) Wrapper<T> queryWrapper, ResultHandler<E> resultHandler);

    /**
     * 根据 entity 条件，查询全部记录（并翻页）
     *
     * @param page         分页查询条件
     * @param queryWrapper 实体对象封装操作类（可以为 null）
     */
    default <P extends IPage<T>> P selectPage(P page, @Param(Constants.WRAPPER) Wrapper<T> queryWrapper) {
        page.setRecords(selectList(page, queryWrapper));
        return page;
    }

    /**
     * 根据 Wrapper 条件，查询全部记录（并翻页）
     *
     * @param page         分页查询条件
     * @param queryWrapper 实体对象封装操作类
     */
    default <P extends IPage<Map<String, Object>>> P selectMapsPage(P page, @Param(Constants.WRAPPER) Wrapper<T> queryWrapper) {
        page.setRecords(selectMaps(page, queryWrapper));
        return page;
    }

}
```

因此我们只需要将自定义的 **Mapper** 实现 **BaseMapper** 接口，就无需自己实现 **CRUD** 。

![配置Mapper](images/frameworks/Java/mybatisplus/a/v5.png)

代码如下：

```java
package com.mybatisplus.mapper;

import com.mybatisplus.domain.entity.UserEntity;
import com.baomidou.mybatisplus.core.mapper.BaseMapper;

public interface UserMapper extends BaseMapper<UserEntity> {
}
```

### ③ 测试

新建测试类，进行 **CURD** 测试：

```java
package com.mybatisplus;

import cn.hutool.json.JSONUtil;
import com.baomidou.mybatisplus.core.conditions.query.QueryWrapper;
import com.baomidou.mybatisplus.core.metadata.OrderItem;
import com.baomidou.mybatisplus.core.toolkit.Wrappers;
import com.baomidou.mybatisplus.extension.plugins.pagination.Page;
import com.mybatisplus.domain.entity.AddressEntity;
import com.mybatisplus.domain.entity.UserEntity;
import com.mybatisplus.eum.UserStatus;
import com.mybatisplus.mapper.UserMapper;
import com.mybatisplus.service.IAddressService;
import com.mybatisplus.service.IUserService;
import jakarta.annotation.Resource;
import org.apache.catalina.User;
import org.junit.jupiter.api.Test;
import org.springframework.boot.test.context.SpringBootTest;

import java.util.ArrayList;
import java.util.Date;
import java.util.List;

@SpringBootTest(classes = MyBatisPlusApplication.class)
class MyBatisPlusApplicationTests {

    @Resource
    private UserMapper userMapper;
    @Resource
    private IUserService userService;
    @Resource
    private IAddressService addressService;

    /**
     * ①查询出名字中带o的,存款大于等于1000元的用户
     */
    @Test
    void testQueryMapper() {
        List<UserEntity> userEntityList = userMapper.selectList(Wrappers.lambdaQuery(UserEntity.class)
                .like(UserEntity::getUsername, "o")
                .ge(UserEntity::getBalance, 1000));
        System.out.println("userEntityList ===> "+userEntityList);
    }

    /**
     * ②更新用户名为Jack的用户余额为2000
     */
    @Test
    void testUpdateMapper() {
        userMapper.update(Wrappers.lambdaUpdate(UserEntity.class)
                .set(UserEntity::getBalance, 2000)
                .eq(UserEntity::getUsername, "Jack"));
    }

    /**
     * ③基于UpdateWrapper的更新 更新id为1、2、4的用户余额,扣200
     */
    @Test
    void testUpdateWrapper() {
        userMapper.update(null, Wrappers.<UserEntity>update().lambda()
                .setSql("balance = balance - 200")
                .in(UserEntity::getId, 1, 2, 4));
    }

    /**
     * 自定义SQL
     */
    @Test
    void testCustomWrapper() {
        // 1.准备自定义查询条件
        List<Long> ids = List.of(1L, 2L, 4L);
        // 2、定义条件
        QueryWrapper<UserEntity> wrapper = new QueryWrapper<UserEntity>().in("id", ids);
        // 3.调用mapper的自定义方法，直接传递Wrapper
        userMapper.deductBalanceByIds(200, wrapper);
    }

    /**
     * 批量新增用户
     */
    @Test
    void testInsertBatch() {
        List<UserEntity> userEntityList = new ArrayList<>(1000);
        long l = System.currentTimeMillis();
        for (int i = 0; i < 100000; i++) {
            UserEntity userEntity = new UserEntity();
            userEntity.setUsername("user_" + i);
            userEntity.setBalance(1000+i);
//            userEntity.setInfo(1);
            userEntity.setPhone("phone_"+i);
            userEntity.setStatus(UserStatus.NORMAL);
            userEntity.setPassword("password_"+i);
            userEntity.setCreateTime(new Date());
            userEntity.setUpdateTime(new Date());
//            userEntity.setInfo(JSONUtil.toJsonStr(1));
            userEntityList.add(userEntity);
            if (i%1000 == 0) {
                userService.saveBatch(userEntityList);
                //4、清空集合,准备下一批数据
                userEntityList.clear();
            }
        }
        long l1 = System.currentTimeMillis();
        System.out.println("耗时："+(l1-l));
    }

    /**
     * 地址逻辑删除
     */
    @Test
    void testDelete() {
        //1、删除
        addressService.removeById(59L);

        //2、查询
        AddressEntity addressEntity = addressService.getById(59L);
        System.out.println("addressEntity ===> "+addressEntity);
    }

    /**
     * 枚举处理测试
     */
    @Test
    void testService() {
        List<UserEntity> list = userService.list();
        list.forEach(System.out::println);
    }

    /**
     * 分页测试
     */
    @Test
    void testPageQuery() {
        // 1.分页查询，new Page()的两个参数分别是：页码、每页大小
        int current = 1;
        int size = 2;
        Page<UserEntity> page = Page.of(current, size);
        // 1.2、排序
        page.addOrder(OrderItem.asc("balance"));
        page.addOrder(OrderItem.desc("id"));
        Page<UserEntity> p = userService.page(page);
        // 2.总条数
        System.out.println("total = " + p.getTotal());
        // 3.总页数
        System.out.println("pages = " + p.getPages());

        // 4.数据
        List<UserEntity> records = p.getRecords();
        records.forEach(System.out::println);
    }
}
```



## Ⅲ 常见注解

在上述的案例中我们发现仅仅引入了依赖，继承了 **BaseMapper** 就能够使用 **MybatisPlus** 。但是问题是：

**MybatisPlus** 是怎么知道我们要查询的是哪张表呢？表中有哪些字段呢？

其实在我们继承 BaseMapper 的时候，就给其指定了一个泛型：

![配置Mapper](images/frameworks/Java/mybatisplus/a/v5.png)

泛型中的 **UserEntity** 就是与数据库对应的 **PO** 实体

**MybatisPlus** 就是根据 **PO** 实体的信息来推断出数据库表的信息，从而生成 **SQL**，默认情况是：

- **MybatisPlus** 会把 **PO** 实体的类名驼峰转下划线作为表名
- **MybatisPlus** 会把 **PO** 实体的所有变量名驼峰转下划线作为表的字段名，并根据变量类型推断字段类型
- **MybatisPlus** 会把名为 **id** 的字段作为主键

但在很多情况下，默认的实现与我们的实际场景不符，因此 **MybatisPlus** 提供了一些注解来让我们进行声明



### ① @TableName

- 描述：表名注解，标识实体类对应的表
- 使用位置：实体类

示例：

```java
@TableName("user")
public class User {
    private Long id;
    private String name;
}
```

**TableName** 的属性：

| **属性**         | **类型** | **必须指定** | **默认值** | **描述**                                                     |
| ---------------- | -------- | ------------ | ---------- | ------------------------------------------------------------ |
| value            | String   | 否           | ""         | 表名                                                         |
| schema           | String   | 否           | ""         | schema                                                       |
| keepGlobalPrefix | boolean  | 否           | false      | 是否保持使用全局的 tablePrefix 的值（当全局 tablePrefix 生效时） |
| resultMap        | String   | 否           | ""         | xml 中 resultMap 的 id（用于满足特定类型的实体类对象绑定）   |
| autoResultMap    | boolean  | 否           | false      | 是否自动构建 resultMap 并使用（如果设置 resultMap 则不会进行 resultMap 的自动构建与注入） |
| excludeProperty  | String[] | 否           | {}         | 需要排除的属性名 @since 3.3.1                                |



### ② @TableId

- 描述：主键注解，标识实体类中的主键字段
- 使用位置：实体类的主键字段

示例：

```Java
@TableName("user")
public class User {
    @TableId
    private Long id;
    private String name;
}
```

**TableId** 的属性：

| **属性** | **类型** | **必须指定** | **默认值**  | **描述**     |
| :------- | :------- | :----------- | :---------- | :----------- |
| value    | String   | 否           | ""          | 表名         |
| type     | Enum     | 否           | IdType.NONE | 指定主键类型 |

**IdType **支持的类型有：

| **值**        | **描述**                                                     |
| :------------ | :----------------------------------------------------------- |
| AUTO          | 数据库 ID 自增                                               |
| NONE          | 无状态，该类型为未设置主键类型（注解里等于跟随全局，全局里约等于 INPUT） |
| INPUT         | insert 前自行 set 主键值                                     |
| ASSIGN_ID     | 分配 ID(主键类型为 Number(Long 和 Integer)或 String)(since 3.3.0),使用接口IdentifierGenerator的方法nextId(默认实现类为DefaultIdentifierGenerator雪花算法) |
| ASSIGN_UUID   | 分配 UUID,主键类型为 String(since 3.3.0),使用接口IdentifierGenerator的方法nextUUID(默认 default 方法) |
| ID_WORKER     | 分布式全局唯一 ID 长整型类型(please use ASSIGN_ID)           |
| UUID          | 32 位 UUID 字符串(please use ASSIGN_UUID)                    |
| ID_WORKER_STR | 分布式全局唯一 ID 字符串类型(please use ASSIGN_ID)           |

这里比较常见的有三种：

- `AUTO`：利用数据库的id自增长
- `INPUT`：手动生成id
- `ASSIGN_ID`：雪花算法生成`Long`类型的全局唯一id，这是默认的ID策略



### ③ @TableField

- 描述：普通字段的注解（与数据库字段匹配）
- 使用位置：`PO` 实体的普通字段

示例：

```Java
@TableName("user")
public class User {
    @TableId
    private Long id;
    private String name;
    private Integer age;
    @TableField("isMarried")
    private Boolean isMarried;
    @TableField("concat")
    private String concat;
}
```

**TableField** 的属性：

| **属性**         | **类型**   | **必填** | **默认值**            | **描述**                                                     |
| ---------------- | ---------- | -------- | --------------------- | ------------------------------------------------------------ |
| value            | String     | 否       | ""                    | 数据库字段值                                                 |
| exist            | boolean    | 否       | true                  | 是否为数据库表字段                                           |
| condition        | String     | 否       | ""                    | 字段 where 实体查询比较条件，有值设置则按设置的值为准，没有则为默认全局 |
| update           | String     | 否       | ""                    | 字段 update set 部分注入，例如：当在version字段上注解update="%s+1" 表示更新时会 set version=version+1 （该属性优先级高于 el 属性） |
| insertStrategy   | Enum       | 否       | FieldStrategy.DEFAULT | 字段验证策略之 insert: 当insert操作时，该字段拼接insert语句时的策略 |
| updateStrategy   | Enum       | 否       | FieldStrategy.DEFAULT | 字段验证策略之 update: 当更新操作时，该字段拼接set语句时的策略 |
| whereStrategy    | Enum       | 否       | FieldStrategy.DEFAULT | 字段验证策略之 where: 表示该字段在拼接where条件时的策略      |
| fill             | Enum       | 否       | FieldFill.DEFAULT     | 字段自动填充策略                                             |
| select           | boolean    | 否       | true                  | 是否进行 select 查询                                         |
| keepGlobalFormat | boolean    | 否       | false                 | 是否保持使用全局的 format 进行处理                           |
| jdbcType         | JdbcType   | 否       | JdbcType.UNDEFINED    | JDBC 类型 (该默认值不代表会按照该值生效)                     |
| typeHandler      | TypeHander | 否       |                       | 类型处理器 (该默认值不代表会按照该值生效)                    |
| numericScale     | String     | 否       | ""                    | 指定小数点后保留的位数                                       |



## Ⅳ 常见配置

```yaml
mybatis-plus:
  # 全局配置文件位置（可选）
  config-location: classpath:mybatis/mybatis-config.xml
  
  # Mapper XML文件位置
  mapper-locations: classpath:mapper/**/*.xml
  
  # 配置实体类所在的包名，MyBatis-Plus会自动扫描并注册为别名
  type-aliases-package: com.example.yourproject.model

  # 全局配置
  global-config:
    db-config:
      id-type: auto # 全局id类型为自增长
      table-prefix: tbl_ # 配置表前缀
    # 开启驼峰命名规则转换
    capital-mode: true
    # 配置逻辑删除相关属性
    logic-delete-field: deleted
    logic-delete-value: 1
    logic-not-delete-value: 0
  
  # 自定义枚举类型转换器
  configuration:
    default-enum-type-handler: com.baomidou.mybatisplus.core.handlers.MybatisEnumTypeHandler

  # 分页插件配置
  pagination:
    enabled: true
    page-size: 10
    reasonable: true
```

- **config-location** ：用于指定 **Mybatis** 配置文件的路径
- **mapper-locations** ：配置 **Mapper** **XML** 文件所在的位置
- **type-aliases-package** ：配置实体类所在的包名，**MybatisPlus** 会自动扫描并注册为别名
- **global-config** ：全局配置
- **configuration** ：自定义配置
- **pagination** ：分页插件配置



大多数的配置都是有默认值的，因此我们都无需配置，但还是有一些没有默认值的，例如：

- 实体类的别名扫描包
- 全局 **id** 类型

```YAML
mybatis-plus:
  type-aliases-package: com.itheima.mp.domain.po
  global-config:
    db-config:
      id-type: auto # 全局id类型为自增长
```

需要注意的是 MybatisPlus 也支持手写 SQL 的，而 mapper 文件的读取地址可以自己配置：

```YAML
mybatis-plus:
  mapper-locations: "classpath*:/mapper/**/*.xml" # Mapper.xml文件地址，当前这个是默认值。
```

可以看到默认值是 `"classpath*:/mapper/**/*.xml"`，也就是说我们需要把 Mapper.xml 文件放在这个位置下被加载

例如：

![yaml配置](images/frameworks/Java/mybatisplus/a/v6.png)



------



# 核心功能



## Ⅰ 条件构造器

除了新增以外，修改、删除、查询的 **SQL** 语句都需要指定 **where** 条件。因此 **BaseMapper** 中提供了了相关的方法除了支持 **id** 还支持更复杂的 **where** 条件。

![BaseMapper](images/frameworks/Java/mybatisplus/a/v7.png)

参数中的 **Wrapper** 就是条件构造的抽象类，其下有很多默认实现，继承关系如下图所示：

![BaseMapper](images/frameworks/Java/mybatisplus/a/v8.png)

**Wrapper** 的子类 **AbstractWrapper** 提供了 **where** 中所包含的所有条件构造方法：

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v9.png)

而 **QueryWrapper** 在 **AbstractWrapper**  基础上拓展了一个 select 方法，用于指定查询字段：

```java
public class QueryWrapper<T> extends AbstractWrapper<T, String, QueryWrapper<T>> implements Query<QueryWrapper<T>, T, String> {
    private final SharedString sqlSelect;

    public QueryWrapper() {
        this((Object)null);
    }

    public QueryWrapper(T entity) {
        this.sqlSelect = new SharedString();
        super.setEntity(entity);
        super.initNeed();
    }

    public QueryWrapper(T entity, String... columns) {
        this.sqlSelect = new SharedString();
        super.setEntity(entity);
        super.initNeed();
        this.select(columns);
    }

    private QueryWrapper(T entity, Class<T> entityClass, AtomicInteger paramNameSeq, Map<String, Object> paramNameValuePairs, MergeSegments mergeSegments, SharedString paramAlias, SharedString lastSql, SharedString sqlComment, SharedString sqlFirst) {
        this.sqlSelect = new SharedString();
        super.setEntity(entity);
        super.setEntityClass(entityClass);
        this.paramNameSeq = paramNameSeq;
        this.paramNameValuePairs = paramNameValuePairs;
        this.expression = mergeSegments;
        this.paramAlias = paramAlias;
        this.lastSql = lastSql;
        this.sqlComment = sqlComment;
        this.sqlFirst = sqlFirst;
    }

    @SafeVarargs
    public final QueryWrapper<T> select(String... columns) {
        return this.select(Arrays.asList(columns));
    }

    public QueryWrapper<T> select(List<String> columns) {
        if (CollectionUtils.isNotEmpty(columns)) {
            this.sqlSelect.setStringValue(String.join(",", columns));
        }

        return (QueryWrapper)this.typedThis;
    }

    public QueryWrapper<T> select(Class<T> entityClass, Predicate<TableFieldInfo> predicate) {
        super.setEntityClass(entityClass);
        this.sqlSelect.setStringValue(TableInfoHelper.getTableInfo(this.getEntityClass()).chooseSelect(predicate));
        return (QueryWrapper)this.typedThis;
    }

    public String getSqlSelect() {
        return this.sqlSelect.getStringValue();
    }

    protected String columnSqlInjectFilter(String column) {
        return StringUtils.sqlInjectionReplaceBlank(column);
    }

    public LambdaQueryWrapper<T> lambda() {
        return new LambdaQueryWrapper(this.getEntity(), this.getEntityClass(), this.sqlSelect, this.paramNameSeq, this.paramNameValuePairs, this.expression, this.paramAlias, this.lastSql, this.sqlComment, this.sqlFirst);
    }

    protected QueryWrapper<T> instance() {
        return new QueryWrapper(this.getEntity(), this.getEntityClass(), this.paramNameSeq, this.paramNameValuePairs, new MergeSegments(), this.paramAlias, SharedString.emptyString(), SharedString.emptyString(), SharedString.emptyString());
    }

    public void clear() {
        super.clear();
        this.sqlSelect.toNull();
    }
}
```

而 **UpdateWrapper** 则在 **AbstractWrapper**  基础上拓展了了一个 **set** 方法，用于指定 **SQL** 中的 **SET** 部分：

```java
public class UpdateWrapper<T> extends AbstractWrapper<T, String, UpdateWrapper<T>> implements Update<UpdateWrapper<T>, String> {
    private final List<String> sqlSet;

    public UpdateWrapper() {
        this((Object)null);
    }

    public UpdateWrapper(T entity) {
        super.setEntity(entity);
        super.initNeed();
        this.sqlSet = new ArrayList();
    }

    private UpdateWrapper(T entity, List<String> sqlSet, AtomicInteger paramNameSeq, Map<String, Object> paramNameValuePairs, MergeSegments mergeSegments, SharedString paramAlias, SharedString lastSql, SharedString sqlComment, SharedString sqlFirst) {
        super.setEntity(entity);
        this.sqlSet = sqlSet;
        this.paramNameSeq = paramNameSeq;
        this.paramNameValuePairs = paramNameValuePairs;
        this.expression = mergeSegments;
        this.paramAlias = paramAlias;
        this.lastSql = lastSql;
        this.sqlComment = sqlComment;
        this.sqlFirst = sqlFirst;
    }

    public String getSqlSet() {
        return CollectionUtils.isEmpty(this.sqlSet) ? null : String.join(",", this.sqlSet);
    }

    public UpdateWrapper<T> set(boolean condition, String column, Object val, String mapping) {
        return (UpdateWrapper)this.maybeDo(condition, () -> {
            String sql = this.formatParam(mapping, val);
            this.sqlSet.add(column + "=" + sql);
        });
    }

    public UpdateWrapper<T> setSql(boolean condition, String sql) {
        if (condition && StringUtils.isNotBlank(sql)) {
            this.sqlSet.add(sql);
        }

        return (UpdateWrapper)this.typedThis;
    }

    protected String columnSqlInjectFilter(String column) {
        return StringUtils.sqlInjectionReplaceBlank(column);
    }

    public LambdaUpdateWrapper<T> lambda() {
        return new LambdaUpdateWrapper(this.getEntity(), this.getEntityClass(), this.sqlSet, this.paramNameSeq, this.paramNameValuePairs, this.expression, this.paramAlias, this.lastSql, this.sqlComment, this.sqlFirst);
    }

    protected UpdateWrapper<T> instance() {
        return new UpdateWrapper(this.getEntity(), (List)null, this.paramNameSeq, this.paramNameValuePairs, new MergeSegments(), this.paramAlias, SharedString.emptyString(), SharedString.emptyString(), SharedString.emptyString());
    }

    public void clear() {
        super.clear();
        this.sqlSet.clear();
    }
}
```



### ① QueryWrapper

无论是修改、更新、查询，都可以使用 QueryWrapper 来构建查询条件。

**查询：**

```java
/**
 * ①查询出名字中带o的,存款大于等于1000元的用户
 */
@Test
void testQueryWrapper() {
    // 1.构建查询条件 where name like "%o%" AND balance >= 1000
    QueryWrapper<User> wrapper = new QueryWrapper<User>()
            .select("id", "username", "info", "balance")
            .like("username", "o")
            .ge("balance", 1000);
    // 2.查询数据
    List<User> users = userMapper.selectList(wrapper);
    users.forEach(System.out::println);
}
```

**更新：**

```java
/**
 * ②更新用户名为Jack的用户余额为2000
 */
@Test
void testUpdateByQueryWrapper() {
    // 1.构建查询条件 where name = "Jack"
    QueryWrapper<User> wrapper = new QueryWrapper<User>().eq("username", "Jack");
    // 2.更新数据，user中非null字段都会作为set语句
    User user = new User();
    user.setBalance(2000);
    userMapper.update(user, wrapper);
}
```

### ② UpdateWrapper

```java
/**
 * ③基于UpdateWrapper的更新 更新id为1、2、4的用户余额,扣200
 */
@Test
void testUpdateWrapper() {
    userMapper.update(null, Wrappers.<UserEntity>update().lambda()
            .setSql("balance = balance - 200")
            .in(UserEntity::getId, 1, 2, 4));
}
```



### ③ LambdaQueryWrapper

其中一种办法是基于变量的 **gettter** 方法结合反射技术。因此我们只要将条件对应的字段的 **gettter** 方法传递给 **MybatisPlus** ，它就能计算出对应的变量名了。而传递方法可以使用 **JDK8** 中的`方法引用`和 **Lambda** 表达式。 因此 **MybatisPlus** 又提供了一套基于 **Lambda** 的 **Wrapper** ，包含两个：

- **LambdaQueryWrapper**
- **LambdaUpdateWrapper**

分别对应 **QueryWrapper** 和 **UpdateWrappe**

```java
/**
 * ①查询出名字中带o的,存款大于等于1000元的用户
 */
@Test
void testQueryMapper() {
    List<UserEntity> userEntityList = userMapper.selectList(Wrappers.lambdaQuery(UserEntity.class)
            .like(UserEntity::getUsername, "o")
            .ge(UserEntity::getBalance, 1000));
    System.out.println("userEntityList ===> "+userEntityList);
}

/**
 * ②更新用户名为Jack的用户余额为2000
 */
@Test
void testUpdateMapper() {
    userMapper.update(Wrappers.lambdaUpdate(UserEntity.class)
            .set(UserEntity::getBalance, 2000)
            .eq(UserEntity::getUsername, "Jack"));
}

/**
 * ③基于UpdateWrapper的更新 更新id为1、2、4的用户余额,扣200
 */
@Test
void testUpdateWrapper() {
    userMapper.update(null, Wrappers.<UserEntity>update().lambda()
            .setSql("balance = balance - 200")
            .in(UserEntity::getId, 1, 2, 4));
}
```



## Ⅱ 自定义 SQL

**MybatisPlus** 提供了自定义 **SQL** 功能，可以让我们先利用 **Wrapper** 来构建查询条件，然后再结合 **Mapper.xml** 来编写 **SQL**



### ① 基本用法

先构建查询条件：

```java
/**
 * 自定义SQL
 */
@Test
void testCustomWrapper() {
    // 1.准备自定义查询条件
    List<Long> ids = List.of(1L, 2L, 4L);
    // 2、定义条件
    QueryWrapper<UserEntity> wrapper = new QueryWrapper<UserEntity>().in("id", ids);
    // 3.调用mapper的自定义方法，直接传递Wrapper
    userMapper.deductBalanceByIds(200, wrapper);
}
```

再在 **UserMapper** 中定义 **SQL**：

```java
public interface UserMapper extends BaseMapper<UserEntity> {

    @Select("UPDATE user SET balance = balance - #{money} ${ew.customSqlSegment}")
    void deductBalanceByIds(@Param("money") int money, @Param("ew") QueryWrapper<UserEntity> wrapper);
}
```



### ② 多表关联

理论上来说 **MybatisPlus** 是单表操作不支持多表关联的，不过我们可以利用 **Wrapper** 中自定义条件结合自定义 **SQL** 来实现多表查询的效果。

例如，我们要查出所有收获地址在北京并且用户 **id** 在 1、2、4 的用户

如果是基于 **mybatis** 实现 **SQL**：

```XML
<select id="queryUserByIdAndAddr" resultType="com.itheima.mp.domain.po.User">
      SELECT *
      FROM user u
      INNER JOIN address a ON u.id = a.user_id
      WHERE u.id
      <foreach collection="ids" separator="," item="id" open="IN (" close=")">
          #{id}
      </foreach>
      AND a.city = #{city}
  </select>
```

我们也可以使用自定义 **SQL** 结合 **Wrapper** ：

先构建查询条件：

```Java
@Test
void testCustomJoinWrapper() {
    // 1.准备自定义查询条件
    QueryWrapper<User> wrapper = new QueryWrapper<User>()
            .in("u.id", List.of(1L, 2L, 4L))
            .eq("a.city", "北京");

    // 2.调用mapper的自定义方法
    List<User> users = userMapper.queryUserByWrapper(wrapper);

    users.forEach(System.out::println);
}
```

再在 **UserMapper** 中自定义 **SQL** 方法：

```Java
@Select("SELECT u.* FROM user u INNER JOIN address a ON u.id = a.user_id ${ew.customSqlSegment}")
List<User> queryUserByWrapper(@Param("ew")QueryWrapper<User> wrapper);
```

当然也可以在 **UserMapper.xml** 中写 **SQL**：

```XML
<select id="queryUserByIdAndAddr" resultType="com.itheima.mp.domain.po.User">
    SELECT * FROM user u INNER JOIN address a ON u.id = a.user_id ${ew.customSqlSegment}
</select>
```



## Ⅲ Service 接口

通用接口为 **Iservice** ，默认实现为 **ServiceImpl **，其中封装方法为一下几类：

- `save`：新增
- `remove`：删除
- `update`：更新
- `get`：查询单个结果
- `list`：查询集合结果
- `count`：计数
- `page`：分页查询



### ① CRUD

```java
public interface IService<T> {
    int DEFAULT_BATCH_SIZE = 1000;

    // save 新增
    default boolean save(T entity) {
        return SqlHelper.retBool(this.getBaseMapper().insert(entity));
    }

    @Transactional(
        rollbackFor = {Exception.class}
    )
    default boolean saveBatch(Collection<T> entityList) {
        return this.saveBatch(entityList, 1000);
    }

    boolean saveBatch(Collection<T> entityList, int batchSize);

    @Transactional(
        rollbackFor = {Exception.class}
    )
    default boolean saveOrUpdateBatch(Collection<T> entityList) {
        return this.saveOrUpdateBatch(entityList, 1000);
    }

    boolean saveOrUpdateBatch(Collection<T> entityList, int batchSize);

    default boolean removeById(Serializable id) {
        return SqlHelper.retBool(this.getBaseMapper().deleteById(id));
    }

    // remove 删除
    default boolean removeById(Serializable id, boolean useFill) {
        throw new UnsupportedOperationException("不支持的方法!");
    }

    default boolean removeById(T entity) {
        return SqlHelper.retBool(this.getBaseMapper().deleteById(entity));
    }

    default boolean removeByMap(Map<String, Object> columnMap) {
        Assert.notEmpty(columnMap, "error: columnMap must not be empty", new Object[0]);
        return SqlHelper.retBool(this.getBaseMapper().deleteByMap(columnMap));
    }

    default boolean remove(Wrapper<T> queryWrapper) {
        return SqlHelper.retBool(this.getBaseMapper().delete(queryWrapper));
    }

    default boolean removeByIds(Collection<?> list) {
        return CollectionUtils.isEmpty(list) ? false : SqlHelper.retBool(this.getBaseMapper().deleteBatchIds(list));
    }

    @Transactional(
        rollbackFor = {Exception.class}
    )
    default boolean removeByIds(Collection<?> list, boolean useFill) {
        if (CollectionUtils.isEmpty(list)) {
            return false;
        } else {
            return useFill ? this.removeBatchByIds(list, true) : SqlHelper.retBool(this.getBaseMapper().deleteBatchIds(list));
        }
    }

    @Transactional(
        rollbackFor = {Exception.class}
    )
    default boolean removeBatchByIds(Collection<?> list) {
        return this.removeBatchByIds(list, 1000);
    }

    @Transactional(
        rollbackFor = {Exception.class}
    )
    default boolean removeBatchByIds(Collection<?> list, boolean useFill) {
        return this.removeBatchByIds(list, 1000, useFill);
    }

    default boolean removeBatchByIds(Collection<?> list, int batchSize) {
        throw new UnsupportedOperationException("不支持的方法!");
    }

    default boolean removeBatchByIds(Collection<?> list, int batchSize, boolean useFill) {
        throw new UnsupportedOperationException("不支持的方法!");
    }

    // update 修改
    default boolean updateById(T entity) {
        return SqlHelper.retBool(this.getBaseMapper().updateById(entity));
    }

    default boolean update(Wrapper<T> updateWrapper) {
        return this.update((Object)null, updateWrapper);
    }

    default boolean update(T entity, Wrapper<T> updateWrapper) {
        return SqlHelper.retBool(this.getBaseMapper().update(entity, updateWrapper));
    }

    @Transactional(
        rollbackFor = {Exception.class}
    )
    default boolean updateBatchById(Collection<T> entityList) {
        return this.updateBatchById(entityList, 1000);
    }

    boolean updateBatchById(Collection<T> entityList, int batchSize);

    boolean saveOrUpdate(T entity);

    // get 查询单个结果
    default T getById(Serializable id) {
        return this.getBaseMapper().selectById(id);
    }

    // list 查询集合结果
    default List<T> listByIds(Collection<? extends Serializable> idList) {
        return this.getBaseMapper().selectBatchIds(idList);
    }

    default List<T> listByMap(Map<String, Object> columnMap) {
        return this.getBaseMapper().selectByMap(columnMap);
    }

    // get 查询单个结果对象
    default T getOne(Wrapper<T> queryWrapper) {
        return this.getOne(queryWrapper, true);
    }

    T getOne(Wrapper<T> queryWrapper, boolean throwEx);

    Map<String, Object> getMap(Wrapper<T> queryWrapper);

    <V> V getObj(Wrapper<T> queryWrapper, Function<? super Object, V> mapper);

    // count 计数
    default long count() {
        return this.count(Wrappers.emptyWrapper());
    }

    default long count(Wrapper<T> queryWrapper) {
        return SqlHelper.retCount(this.getBaseMapper().selectCount(queryWrapper));
    }

    // list 查询集合结果
    default List<T> list(Wrapper<T> queryWrapper) {
        return this.getBaseMapper().selectList(queryWrapper);
    }

    default List<T> list() {
        return this.list(Wrappers.emptyWrapper());
    }

    // Ipage 分页
    default <E extends IPage<T>> E page(E page, Wrapper<T> queryWrapper) {
        return this.getBaseMapper().selectPage(page, queryWrapper);
    }

    default <E extends IPage<T>> E page(E page) {
        return this.page(page, Wrappers.emptyWrapper());
    }

    // list 查询集合结果
    default List<Map<String, Object>> listMaps(Wrapper<T> queryWrapper) {
        return this.getBaseMapper().selectMaps(queryWrapper);
    }

    default List<Map<String, Object>> listMaps() {
        return this.listMaps(Wrappers.emptyWrapper());
    }

    default List<Object> listObjs() {
        return this.listObjs(Function.identity());
    }

    default <V> List<V> listObjs(Function<? super Object, V> mapper) {
        return this.listObjs(Wrappers.emptyWrapper(), mapper);
    }

    default List<Object> listObjs(Wrapper<T> queryWrapper) {
        return this.listObjs(queryWrapper, Function.identity());
    }

    default <V> List<V> listObjs(Wrapper<T> queryWrapper, Function<? super Object, V> mapper) {
        return (List)this.getBaseMapper().selectObjs(queryWrapper).stream().filter(Objects::nonNull).map(mapper).collect(Collectors.toList());
    }

    // Ipage 分页
    default <E extends IPage<Map<String, Object>>> E pageMaps(E page, Wrapper<T> queryWrapper) {
        return this.getBaseMapper().selectMapsPage(page, queryWrapper);
    }

    default <E extends IPage<Map<String, Object>>> E pageMaps(E page) {
        return this.pageMaps(page, Wrappers.emptyWrapper());
    }

    BaseMapper<T> getBaseMapper();

    Class<T> getEntityClass();

    default QueryChainWrapper<T> query() {
        return ChainWrappers.queryChain(this.getBaseMapper());
    }

    default LambdaQueryChainWrapper<T> lambdaQuery() {
        return ChainWrappers.lambdaQueryChain(this.getBaseMapper(), this.getEntityClass());
    }

    default LambdaQueryChainWrapper<T> lambdaQuery(T entity) {
        return ChainWrappers.lambdaQueryChain(this.getBaseMapper(), entity);
    }

    default KtQueryChainWrapper<T> ktQuery() {
        return ChainWrappers.ktQueryChain(this.getBaseMapper(), this.getEntityClass());
    }

    default KtUpdateChainWrapper<T> ktUpdate() {
        return ChainWrappers.ktUpdateChain(this.getBaseMapper(), this.getEntityClass());
    }

    default UpdateChainWrapper<T> update() {
        return ChainWrappers.updateChain(this.getBaseMapper());
    }

    default LambdaUpdateChainWrapper<T> lambdaUpdate() {
        return ChainWrappers.lambdaUpdateChain(this.getBaseMapper());
    }

    default boolean saveOrUpdate(T entity, Wrapper<T> updateWrapper) {
        return this.update(entity, updateWrapper) || this.saveOrUpdate(entity);
    }
}
```

**新增：**

- `save`是新增单个元素
- `saveBatch`是批量新增
- `saveOrUpdate`是根据id判断，如果数据存在就更新，不存在则新增
- `saveOrUpdateBatch`是批量的新增或修改

**删除：**

- `removeById`：根据id删除
- `removeByIds`：根据id批量删除
- `removeByMap`：根据Map中的键值对为条件删除
- `remove(Wrapper<T>)`：根据Wrapper条件删除
- `~~removeBatchByIds~~`：暂不支持

**修改：**

- `updateById`：根据id修改
- `update(Wrapper<T>)`：根据`UpdateWrapper`修改，`Wrapper`中包含`set`和`where`部分
- `update(T，Wrapper<T>)`：按照`T`内的数据修改与`Wrapper`匹配到的数据
- `updateBatchById`：根据id批量修改

**Get：**	

- `getById`：根据id查询1条数据
- `getOne(Wrapper<T>)`：根据`Wrapper`查询1条数据
- `getBaseMapper`：获取`Service`内的`BaseMapper`实现，某些时候需要直接调用`Mapper`内的自定义`SQL`时可以用这个方法获取到`Mapper`

**List：**

- `listByIds`：根据id批量查询
- `list(Wrapper<T>)`：根据Wrapper条件查询多条数据
- `list()`：查询所有

**Count**：

- `count()`：统计所有数量
- `count(Wrapper<T>)`：统计符合`Wrapper`条件的数据数量

**getBaseMapper**：

- 当我们在service中要调用Mapper中自定义SQL时，就必须获取service对应的Mapper，就可以通过这个方法



### ② 基本用法

首先，定义 **IUserService** ，继承 **IService**：

```java
public interface IUserService extends IService<User> {
    // 拓展自定义方法
}
```

然后，编写 **UserServiceImpl** 类，继承 **ServiceImpl** ，实现 **UserService**：

```java
@Service
public class UserServiceImpl extends ServiceImpl<UserMapper, User>implements IUserService {
}
```

项目结构如下：

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v10.png)



接下来，我们快速实现下面4个接口：

| **编号** | **接口**       | **请求方式** | **请求路径** | **请求参数** | **返回值** |
| :------- | :------------- | :----------- | :----------- | :----------- | :--------- |
| 1        | 新增用户       | POST         | /users       | 用户表单实体 | 无         |
| 2        | 删除用户       | DELETE       | /users/{id}  | 用户id       | 无         |
| 3        | 根据id查询用户 | GET          | /users/{id}  | 用户id       | 用户VO     |
| 4        | 根据id批量查询 | GET          | /users       | 用户id集合   | 用户VO集合 |



为了方便测试，引入 **swagger-knife4j：**

依赖：

```XML
<!--swagger-->
<dependency>
    <groupId>com.github.xiaoymin</groupId>
    <artifactId>knife4j-openapi2-spring-boot-starter</artifactId>
    <version>4.1.0</version>
</dependency>
<!--web-->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

**yml** 文件中 **swagger** 配置

```YAML
knife4j:
  enable: true
  openapi:
    title: 用户管理接口文档
    description: "用户管理接口文档"
    email: xxx@qq.com
    concat: violet
    url: https://violet.zeabur.app/
    version: v1.0.0
    group:
      default:
        group-name: default
        api-rule: package
        api-rule-resources:
          - com.mybatisplus.controller
```

**UserController：**

```java
/**
 * 用户控制器
 * @author lixuan
 * @Date 2024/8/7 17:38
 */
@RestController
@RequestMapping("/user")
@Tag(name = "用户控制器")
@RequiredArgsConstructor
public class UserController {

    private static final Logger log = LoggerFactory.getLogger(UserController.class);
    private final IUserService userService;
    private final IAddressService addressService;

    /**
     * 查询用户
     */
    @GetMapping("/getUser/{id}")
    @Operation(summary = "查询用户 getUser/{id}")
    public UserVO getUser(@Parameter(description = "用户ID") @PathVariable("id") Long id) {
        UserEntity userEntity = userService.getById(id);
        return BeanUtil.copyProperties(userEntity, UserVO.class);
    }

    /**
     * 查询所有用户
     */
    @GetMapping("/getAllUser")
    @Operation(summary = "查询所有用户 getAllUser", ignoreJsonView = true)
    public List<UserVO> getAllUser(@ParameterObject UserEntity userEntity) {
        QueryWrapper<UserEntity> queryWrapper = ConditionUtil.buildQueryWrapper(userEntity, UserEntity.class);
        System.out.println("queryWrapper ===> "+queryWrapper);
        List<UserEntity> userEntityList = userService.list(queryWrapper);
        List<UserVO> userVOS = BeanUtil.copyToList(userEntityList, UserVO.class);
        userVOS.forEach(userVO -> System.out.println(userVO.getUsername()));
        return BeanUtil.copyToList(userEntityList, UserVO.class);
    }

    /**
     * 分页查询
     */
    @GetMapping("/getUserByPage")
    @Operation(summary = "分页查询 getUserByPage")
    public Page<UserEntity> getUserByPage(@ParameterObject UserEntity userEntity,@ParameterObject Query query) {
        QueryWrapper<UserEntity> queryWrapper = ConditionUtil.buildQueryWrapper(userEntity, UserEntity.class);
        Page<UserEntity> page = userService.page(new Page<>(query.getCurrent(), query.getSize()), queryWrapper);
        System.out.println("page ===> "+page);
        return userService.page(new Page<>(query.getCurrent(), query.getSize()), queryWrapper);
    }

    /**
     * 新增用户
     */
    @PostMapping("/addUser")
    @Operation(summary = "新增用户 addUser")
    public boolean addUser(@RequestBody UserDTO userDTO) {
        //1、把DTO转换为实体Entity
        UserEntity userEntity = BeanUtil.copyProperties(userDTO, UserEntity.class);
        return userService.save(userEntity);
    }

    /**
     * 修改用户
     */
    @PutMapping("/updateUser")
    @Operation(summary = "修改用户 updateUser")
    public boolean updateUser(@RequestBody UserEntity userEntity) {
        return userService.updateById(userEntity);
    }

    /**
     * 删除用户
     */
    @DeleteMapping("/deleteUser")
    @Operation(summary = "删除用户 deleteUser")
    public boolean deleteUser(@RequestParam Long id) {
        return userService.removeById(id);
    }

    /**
     * 批量删除用户
     */
    @DeleteMapping("/deleteUserBatch")
    @Operation(summary = "批量删除用户 deleteUserBatch")
    public boolean deleteUserBatch(@RequestParam List<Long> ids) {
        return userService.removeByIds(ids);
    }

    /**
     * 扣减用户余额
     */
    @PutMapping("/{id}/deduction/{money}")
    @Operation(summary = "扣减用户余额 {id}/deduction/{money}")
    public boolean deductBalance(
            @Parameter(description = "用户id") @PathVariable("id") Long id,
            @Parameter(description = "扣减金额") @PathVariable("money") Integer money) {
        return userService.deductBalance(id, money);
    }

    /**
     * 查询用户并且对应其地址足迹
     */
    @GetMapping("/getUserAndAddress/{id}")
    @Operation(summary = "查询用户并且对应其地址足迹 getUserAndAddress/{id}")
    public UserVO getUserAndAddress(@Parameter(description = "用户ID") @PathVariable("id") Long id) {
        //获取用户
        UserEntity userEntity = userService.getById(id);
        if (userEntity == null || userEntity.getStatus() == UserStatus.FREEZE) {
            throw new RuntimeException("用户状态异常！！");
        }
        //转换Vo
        UserVO userVO = BeanUtil.copyProperties(userEntity, UserVO.class);
        //获取地址列表
        List<AddressEntity> addressEntityList = addressService.list(Wrappers.lambdaQuery(AddressEntity.class)
                .eq(AddressEntity::getUserId, id));
        //转换列表VO
        if (CollUtil.isNotEmpty(addressEntityList)) {
            List<AddressVO> addressVOList = BeanUtil.copyToList(addressEntityList, AddressVO.class);
            userVO.setAddressList(addressVOList);
        }
        return userVO;
    }

    /**
     * 根据ids批量查询
     */
    @GetMapping("/getUserByIds")
    @Operation(summary = "根据ids批量查询 getUserByIds")
    public List<UserVO> getUserByIds(@RequestParam List<Long> ids) {
        //1、查询用户
        List<UserEntity> userEntityList = userService.listByIds(ids);
        if (CollUtil.isEmpty(userEntityList)) {
            return Collections.emptyList();
        }
        //2查询地址列表
        List<AddressEntity> addressEntityList = addressService.list(Wrappers.lambdaQuery(AddressEntity.class)
                .in(AddressEntity::getUserId, ids));
        //转为Vo列表
        List<UserVO> userVOList = BeanUtil.copyToList(userEntityList, UserVO.class);
        //根据UserId转为Map
        Map<Long, List<AddressEntity>> addressEntityMap = addressEntityList.stream()
                .collect(Collectors.groupingBy(AddressEntity::getUserId));
        userVOList.forEach(userVO -> {
            if (userVO.getStatus() == UserStatus.FREEZE) {
                log.error("用户{}状态异常！！", userVO.getUsername());
            }

            //1、获取对应地址列表
            Optional.ofNullable(addressEntityMap.get(userVO.getId()))
                    .ifPresent(addressEntities -> {
                        //2、转换为Vo地址列表
                        List<AddressVO> addressVOList = BeanUtil.copyToList(addressEntities, AddressVO.class);
                        //3、注入Vo
                        userVO.setAddressList(addressVOList);
                    });
        });
        return userVOList;
    }

    /**
     * 分页查询 page
     */
    @GetMapping("/page")
    @Operation(summary = "分页查询 page")
    public PageDTO<UserVO> queryUsersPage(@ParameterObject UserQuery query){
        log.info("queryUsersPage ===> {}", query);
        Page<UserEntity> userEntityPage = userService.page(new Page<UserEntity>(query.getPageNo(), query.getPageSize())
                        .addOrder(ObjectUtil.isEmpty(query.getSortBy()) ?
                                OrderItem.desc("update_time") :
                                (query.getIsAsc() != null && query.getIsAsc() ?
                                        OrderItem.asc(query.getSortBy()) :
                                        OrderItem.desc(query.getSortBy()))),
                Wrappers.lambdaQuery(UserEntity.class)
                        .like(StrUtil.isNotBlank(query.getName()), UserEntity::getUsername, query.getName())
                        .between(query.getMinBalance() != null && query.getMaxBalance() != null, UserEntity::getBalance, query.getMinBalance(), query.getMaxBalance()));
        System.out.println("userEntityPage = " + userEntityPage.getRecords());
        //转换为Vo
        List<UserVO> userVOList = BeanUtil.copyToList(userEntityPage.getRecords(), UserVO.class);
        PageDTO<UserVO> userVoPageDTO = new PageDTO<>(userEntityPage.getCurrent(), userEntityPage.getSize(), userVOList);
        userVoPageDTO.setTotal(userEntityPage.getTotal());
        System.out.println("userVoPageDTO = " + userVoPageDTO.getPages());
        return userService.queryUsersPage(query);
    }

}
```

**UserVo：**返回用户对象给前端

```java
/**
 * 用户表VO
 * @author lixuan
 * @Date 2024/8/7 17:33
 */
@Data
@EqualsAndHashCode(callSuper = true)
public class UserVO extends UserEntity {

    @Serial
    private static final long serialVersionUID = 1L;

    @Schema(description = "地址列表")
    private List<AddressVO> addressList;

}
```

**IUserService：**

```java
/**
* @author 1045754
* @description 针对表【user(用户表)】的数据库操作Service
* @createDate 2024-08-07 17:27:57
*/
public interface IUserService extends IService<UserEntity> {

    boolean deductBalance(Long id, Integer money);

    PageDTO<UserVO> queryUsersPage(UserQuery query);
}
```

**UserServiceImpl：**

```java
/**
* @author 1045754
* @description 针对表【user(用户表)】的数据库操作Service实现
* @createDate 2024-08-07 17:27:57
*/
@Service
public class UserServiceImpl extends ServiceImpl<UserMapper, UserEntity>
    implements IUserService {

    @Override
    @Transactional(rollbackFor = Exception.class)
    public boolean deductBalance(Long id, Integer money) {
        //1、查询用户
        UserEntity user = getById(id);
        //2、校验用户状态
        if (user == null || user.getStatus().getValue()== 2) {
            throw new RuntimeException("用户状态异常！");
        }
        //3、校验余额是否充足
        if (user.getBalance() < money) {
            throw new RuntimeException("余额不足！");
        }
        //4、扣减余额
        int remainBalance = user.getBalance() - money;
        return lambdaUpdate()
                .set(UserEntity::getBalance,remainBalance)
                .set(remainBalance==0,UserEntity::getStatus,2)
                .eq(UserEntity::getId,id)
                //乐观锁
                .eq(UserEntity::getBalance,user.getBalance())
                .update();
    }

    @Override
    public PageDTO<UserVO> queryUsersPage(UserQuery query) {
        // 1.构建条件
        // 1.1.分页条件
        Page<UserEntity> page = Page.of(query.getPageNo(), query.getPageSize());
        // 1.2.排序条件
        if (query.getSortBy() != null) {
            page.addOrder(query.getIsAsc()!= null&& query.getIsAsc() ? OrderItem.asc(query.getSortBy()) : OrderItem.desc(query.getSortBy()));
        }else{
            // 默认按照更新时间排序
            page.addOrder(OrderItem.desc("update_time"));
        }
        // 2.查询
        page(page);
        // 3.数据非空校验
        List<UserEntity> records = page.getRecords();
        if (records == null || records.size() <= 0) {
            // 无数据，返回空结果
            return new PageDTO<>(page.getTotal(), page.getPages(), Collections.emptyList());
        }
        // 4.有数据，转换
        List<UserVO> list = BeanUtil.copyToList(records, UserVO.class);
        // 5.封装返回
        return new PageDTO<>(page.getTotal(), page.getPages(), list);
    }
}
```

**UserMapper：**

```java
/**
* @author 1045754
* @description 针对表【user(用户表)】的数据库操作Mapper
* @createDate 2024-08-07 17:27:57
* @Entity com.mybatisplus.domain.entity.UserEntity
*/
public interface UserMapper extends BaseMapper<UserEntity> {

    @Select("UPDATE user SET balance = balance - #{money} ${ew.customSqlSegment}")
    void deductBalanceByIds(@Param("money") int money, @Param("ew") QueryWrapper<UserEntity> wrapper);
}
```

可以看到上述接口，通过引入在 **Controller** 层就可以完成业务接口，但是为了能够更加规范，所以对于复杂的业务，我们任然会选择将业务功能放到 **Service** 层去进行业务实现。

### ③ Lambda

**IService** 中还提供了 **Lambda** 方法来简化我们复杂的查询和更新功能。

案例一：实现一个根据复杂条件查询用户的接口，查询条件如下：

- **name** ：用户关键名称，可以为空
- **status** ：用户状态，可以为空
- **minBalance** ：最小余额，可以为空
- **maxBalance** ：最大余额，可以为空

首先定义查询实体，**UserQuery** ：

```Java
import io.swagger.annotations.ApiModel;
import io.swagger.annotations.ApiModelProperty;
import lombok.Data;

@Data
@ApiModel(description = "用户查询条件实体")
public class UserQuery {
    @ApiModelProperty("用户名关键字")
    private String name;
    @ApiModelProperty("用户状态：1-正常，2-冻结")
    private Integer status;
    @ApiModelProperty("余额最小值")
    private Integer minBalance;
    @ApiModelProperty("余额最大值")
    private Integer maxBalance;
}
```

接下来，在 **UserController** 中定义查询方法：

```Java
@GetMapping("/list")
@ApiOperation("根据id集合查询用户")
public List<UserVO> queryUsers(UserQuery query){
    // 1.组织条件
    String username = query.getName();
    Integer status = query.getStatus();
    Integer minBalance = query.getMinBalance();
    Integer maxBalance = query.getMaxBalance();
    LambdaQueryWrapper<User> wrapper = new QueryWrapper<User>().lambda()
            .like(username != null, User::getUsername, username)
            .eq(status != null, User::getStatus, status)
            .ge(minBalance != null, User::getBalance, minBalance)
            .le(maxBalance != null, User::getBalance, maxBalance);
    // 2.查询用户
    List<User> users = userService.list(wrapper);
    // 3.处理vo
    return BeanUtil.copyToList(users, UserVO.class);
}
```

在组织查询的时候，我们加入 `username != null` 这样的参数，表示只有当这个条件成立的时候才会添加到这个查询条件里，类似与 **Mapper.xml** 文件中的 `<if>`标签。这样就实现了动态查询效果。

**Service** 中对`LambdaQueryWrapper`和`LambdaUpdateWrapper`的用法进一步做了简化，不需要使用 **new** 来创建 **Wrapper** ，而是直接调用 **lambdaQuery** 和 **lambdaUpdate** 方法：

**lambdaQuery** ：

```Java
@GetMapping("/list")
@ApiOperation("根据id集合查询用户")
public List<UserVO> queryUsers(UserQuery query){
    // 1.组织条件l
    String username = query.getName();
    Integer status = query.getStatus();
    Integer minBalance = query.getMinBalance();
    Integer maxBalance = query.getMaxBalance();
    // 2.查询用户
    List<User> users = userService.lambdaQuery()
            .like(username != null, User::getUsername, username)
            .eq(status != null, User::getStatus, status)
            .ge(minBalance != null, User::getBalance, minBalance)
            .le(maxBalance != null, User::getBalance, maxBalance)
            .list();
    // 3.处理vo
    return BeanUtil.copyToList(users, UserVO.class);
}
```

可以发现 `lambdaQuery` 方法中除了可以构建条件，还需要在链式编程的最后添加一个`list()`，这是在告诉 `MP` 我们的调用结果需要是一个 `list` 集合。这里不仅可以用`list()`，可选的方法有：

- `.one()`：最多1个结果
- `.list()`：返回集合结果
- `.count()`：返回计数结果

**lambdaUpdate** ：

```Java
@Override
@Transactional
public void deductBalance(Long id, Integer money) {
    // 1.查询用户
    User user = getById(id);
    // 2.校验用户状态
    if (user == null || user.getStatus() == 2) {
        throw new RuntimeException("用户状态异常！");
    }
    // 3.校验余额是否充足
    if (user.getBalance() < money) {
        throw new RuntimeException("用户余额不足！");
    }
    // 4.扣减余额 update tb_user set balance = balance - ?
    int remainBalance = user.getBalance() - money;
    lambdaUpdate()
            .set(User::getBalance, remainBalance) // 更新余额
            .set(remainBalance == 0, User::getStatus, 2) // 动态判断，是否更新status
            .eq(User::getId, id)
            .eq(User::getBalance, user.getBalance()) // 乐观锁
            .update();
}
```



### ④ 批量新增

逐条插入：

```Java
@Test
void testSaveOneByOne() {
    long b = System.currentTimeMillis();
    for (int i = 1; i <= 100000; i++) {
        userService.save(buildUser(i));
    }
    long e = System.currentTimeMillis();
    System.out.println("耗时：" + (e - b));
}

private User buildUser(int i) {
    User user = new User();
    user.setUsername("user_" + i);
    user.setPassword("123");
    user.setPhone("" + (18688190000L + i));
    user.setBalance(2000);
    user.setInfo("{\"age\": 24, \"intro\": \"英文老师\", \"gender\": \"female\"}");
    user.setCreateTime(LocalDateTime.now());
    user.setUpdateTime(user.getCreateTime());
    return user;
}
```

- 耗时长
- 速度慢

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v11.png)

批量插入：

```Java
@Test
void testSaveBatch() {
    // 准备10万条数据
    List<User> list = new ArrayList<>(1000);
    long b = System.currentTimeMillis();
    for (int i = 1; i <= 100000; i++) {
        list.add(buildUser(i));
        // 每1000条批量插入一次
        if (i % 1000 == 0) {
            userService.saveBatch(list);
            list.clear();
        }
    }
    long e = System.currentTimeMillis();
    System.out.println("耗时：" + (e - b));
}
```

- 耗时较短
- 速度较快

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v12.png)

可以看到批处理后，比逐条新增的效率提高了10倍左右，性能还是不错的。

不过我们查看 **MybatisPlus** 源码：

```Java
@Transactional(rollbackFor = Exception.class)
@Override
public boolean saveBatch(Collection<T> entityList, int batchSize) {
    String sqlStatement = getSqlStatement(SqlMethod.INSERT_ONE);
    return executeBatch(entityList, batchSize, (sqlSession, entity) -> sqlSession.insert(sqlStatement, entity));
}
// ...SqlHelper
public static <E> boolean executeBatch(Class<?> entityClass, Log log, Collection<E> list, int batchSize, BiConsumer<SqlSession, E> consumer) {
    Assert.isFalse(batchSize < 1, "batchSize must not be less than one");
    return !CollectionUtils.isEmpty(list) && executeBatch(entityClass, log, sqlSession -> {
        int size = list.size();
        int idxLimit = Math.min(batchSize, size);
        int i = 1;
        for (E element : list) {
            consumer.accept(sqlSession, element);
            if (i == idxLimit) {
                sqlSession.flushStatements();
                idxLimit = Math.min(idxLimit + batchSize, size);
            }
            i++;
        }
    });
}
```

可以发现其实 **MybatisPlus** 的批处理是基于 **PrepareStatement** 的预编译模式，然后批量提交，最终在数据库执行时还是会有多条 **insert** 语句，逐条插入数据。

```SQL
Preparing: INSERT INTO user ( username, password, phone, info, balance, create_time, update_time ) VALUES ( ?, ?, ?, ?, ?, ?, ? )
Parameters: user_1, 123, 18688190001, "", 2000, 2023-07-01, 2023-07-01
Parameters: user_2, 123, 18688190002, "", 2000, 2023-07-01, 2023-07-01
Parameters: user_3, 123, 18688190003, "", 2000, 2023-07-01, 2023-07-01
```

而如果想要得到最佳性能，最好将多条 SQL 合并为一条：

```SQL
INSERT INTO user ( username, password, phone, info, balance, create_time, update_time )
VALUES 
(user_1, 123, 18688190001, "", 2000, 2023-07-01, 2023-07-01),
(user_2, 123, 18688190002, "", 2000, 2023-07-01, 2023-07-01),
(user_3, 123, 18688190003, "", 2000, 2023-07-01, 2023-07-01),
(user_4, 123, 18688190004, "", 2000, 2023-07-01, 2023-07-01);
```

该怎么做呢？

**MySQL** 的客户端连接参数中，有一个 **rewriteBatchedStatements** ，顾名思义，就是重写批处理 **statement** 语句。

修改 `application.yml` 在 `jdbc` 的 `url` 后面添加参数`&rewriteBatchedStatements=true` ：

```yaml
spring:
  datasource:
    driver-class-name: com.mysql.jdbc.Driver
    url: jdbc:mysql://127.0.0.1:3306/mp?useSSL=false&useUnicode=true&characterEncoding=utf-8&zeroDateTimeBehavior=convertToNull&transformedBitIsBoolean=true&tinyInt1isBit=false&allowMultiQueries=true&serverTimezone=GMT%2B8&allowPublicKeyRetrieval=true&rewriteBatchedStatements=true
    username: root
    password: 123456
```

再次测试插入10万条数据，可以发现速度有明显的提升：

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v13.png)

在`ClientPreparedStatement`的`executeBatchInternal`中，有判断`rewriteBatchedStatements`值是否为true并重写SQL的功能：

最终，`SQL` 被重写了：

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v14.png)



# 扩展功能



## Ⅰ代码生成

在使用 **MybatisPlus** 以后，基础的 **Mapper** 、**Servce** 、**PO** 代码相对固定，重复编写也比较麻烦。

推荐利用 **MyBatisX** 插件进行代码生成：

### ① 插件安装

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v15.png)

### ② 使用

#### **IDEA** 集成数据库：

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v19.png)

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v20.png)

#### 选择生成数据：

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v16.png)

1. 点击右侧 **Database** 展开连接数据库
2. 选择所需生成业务表，右键
3. 点击 **MybatisX-Generator** 打开代码生成窗口

#### 配置代码生成：

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v17.png)

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v18.png)

#### 生成结果：

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v21.png)



## Ⅱ 静态工具

有的时候 Service 之间也会相互调用，为了避免出现循环依赖问题，MybatisPlus 提供了一个静态工具类：Db ，其中的一些静态方法与 IService 中方法签名基本一致，也可以帮助我们实现 CRUD 功能：

```java
/**
 * 以静态方式调用Service中的函数
 *
 * @author VampireAchao
 * @since 2022-05-03
 */
public class Db {

    private static final Log log = LogFactory.getLog(Db.class);

    private Db() {
        /* Do not new me! */
    }

    /**
     * 插入一条记录（选择字段，策略插入）
     *
     * @param entity 实体对象
     */
    public static <T> boolean save(T entity) {
        if (Objects.isNull(entity)) {
            return false;
        }
        Integer result = SqlHelper.execute(getEntityClass(entity), baseMapper -> baseMapper.insert(entity));
        return SqlHelper.retBool(result);
    }

    /**
     * 插入（批量）
     *
     * @param entityList 实体对象集合
     */
    public static <T> boolean saveBatch(Collection<T> entityList) {
        return saveBatch(entityList, IService.DEFAULT_BATCH_SIZE);
    }

    /**
     * 插入（批量）
     *
     * @param entityList 实体对象集合
     * @param batchSize  插入批次数量
     */
    public static <T> boolean saveBatch(Collection<T> entityList, int batchSize) {
        if (CollectionUtils.isEmpty(entityList)) {
            return false;
        }
        Class<T> entityClass = getEntityClass(entityList);
        Class<?> mapperClass = ClassUtils.toClassConfident(getTableInfo(entityClass).getCurrentNamespace());
        String sqlStatement = SqlHelper.getSqlStatement(mapperClass, SqlMethod.INSERT_ONE);
        return SqlHelper.executeBatch(entityClass, log, entityList, batchSize, (sqlSession, entity) -> sqlSession.insert(sqlStatement, entity));
    }

    /**
     * 批量修改插入
     *
     * @param entityList 实体对象集合
     */
    public static <T> boolean saveOrUpdateBatch(Collection<T> entityList) {
        return saveOrUpdateBatch(entityList, IService.DEFAULT_BATCH_SIZE);
    }

    /**
     * 批量修改插入
     *
     * @param entityList 实体对象集合
     * @param batchSize  每次的数量
     */
    public static <T> boolean saveOrUpdateBatch(Collection<T> entityList, int batchSize) {
        if (CollectionUtils.isEmpty(entityList)) {
            return false;
        }
        Class<T> entityClass = getEntityClass(entityList);
        TableInfo tableInfo = getTableInfo(entityClass);
        Class<?> mapperClass = ClassUtils.toClassConfident(tableInfo.getCurrentNamespace());
        String keyProperty = tableInfo.getKeyProperty();
        Assert.notEmpty(keyProperty, "error: can not execute. because can not find column for primary key from entity!");
        return SqlHelper.saveOrUpdateBatch(entityClass, mapperClass, log, entityList, batchSize, (sqlSession, entity) -> {
            Object idVal = tableInfo.getPropertyValue(entity, keyProperty);
            return StringUtils.checkValNull(idVal)
                || CollectionUtils.isEmpty(sqlSession.selectList(SqlHelper.getSqlStatement(mapperClass, SqlMethod.SELECT_BY_ID), entity));
        }, (sqlSession, entity) -> {
            MapperMethod.ParamMap<T> param = new MapperMethod.ParamMap<>();
            param.put(Constants.ENTITY, entity);
            sqlSession.update(SqlHelper.getSqlStatement(mapperClass, SqlMethod.UPDATE_BY_ID), param);
        });
    }

    /**
     * 根据 ID 删除
     *
     * @param id          主键ID
     * @param entityClass 实体类
     */
    public static <T> boolean removeById(Serializable id, Class<T> entityClass) {
        return SqlHelper.execute(entityClass, baseMapper -> SqlHelper.retBool(baseMapper.deleteById(id)));
    }

    /**
     * 根据实体(ID)删除
     *
     * @param entity 实体
     */
    public static <T> boolean removeById(T entity) {
        if (Objects.isNull(entity)) {
            return false;
        }
        return SqlHelper.execute(getEntityClass(entity), baseMapper -> SqlHelper.retBool(baseMapper.deleteById(entity)));
    }

    /**
     * 根据 entity 条件，删除记录
     *
     * @param queryWrapper 实体包装类 {@link com.baomidou.mybatisplus.core.conditions.query.QueryWrapper}
     */
    public static <T> boolean remove(AbstractWrapper<T, ?, ?> queryWrapper) {
        return SqlHelper.execute(getEntityClass(queryWrapper), baseMapper -> SqlHelper.retBool(baseMapper.delete(queryWrapper)));
    }

    /**
     * 根据 ID 选择修改
     *
     * @param entity 实体对象
     */
    public static <T> boolean updateById(T entity) {
        if (Objects.isNull(entity)) {
            return false;
        }
        return SqlHelper.execute(getEntityClass(entity), baseMapper -> SqlHelper.retBool(baseMapper.updateById(entity)));
    }

    /**
     * 根据 UpdateWrapper 条件，更新记录 需要设置sqlset
     *
     * @param updateWrapper 实体对象封装操作类 {@link com.baomidou.mybatisplus.core.conditions.update.UpdateWrapper}
     */
    public static <T> boolean update(AbstractWrapper<T, ?, ?> updateWrapper) {
        return update(null, updateWrapper);
    }

    /**
     * 根据 whereEntity 条件，更新记录
     *
     * @param entity        实体对象
     * @param updateWrapper 实体对象封装操作类 {@link com.baomidou.mybatisplus.core.conditions.update.UpdateWrapper}
     */
    public static <T> boolean update(T entity, AbstractWrapper<T, ?, ?> updateWrapper) {
        return SqlHelper.execute(getEntityClass(updateWrapper), baseMapper -> SqlHelper.retBool(baseMapper.update(entity, updateWrapper)));
    }

    /**
     * 根据ID 批量更新
     *
     * @param entityList 实体对象集合
     */
    public static <T> boolean updateBatchById(Collection<T> entityList) {
        return updateBatchById(entityList, IService.DEFAULT_BATCH_SIZE);
    }

    /**
     * 根据ID 批量更新
     *
     * @param entityList 实体对象集合
     * @param batchSize  更新批次数量
     */
    public static <T> boolean updateBatchById(Collection<T> entityList, int batchSize) {
        Class<T> entityClass = getEntityClass(entityList);
        TableInfo tableInfo = getTableInfo(entityClass);
        String sqlStatement = SqlHelper.getSqlStatement(ClassUtils.toClassConfident(tableInfo.getCurrentNamespace()), SqlMethod.UPDATE_BY_ID);
        return SqlHelper.executeBatch(entityClass, log, entityList, batchSize, (sqlSession, entity) -> {
            MapperMethod.ParamMap<T> param = new MapperMethod.ParamMap<>();
            param.put(Constants.ENTITY, entity);
            sqlSession.update(sqlStatement, param);
        });
    }

    /**
     * 删除（根据ID 批量删除）
     *
     * @param list        主键ID或实体列表
     * @param entityClass 实体类
     */
    public static <T> boolean removeByIds(Collection<? extends Serializable> list, Class<T> entityClass) {
        return SqlHelper.execute(entityClass, baseMapper -> SqlHelper.retBool(baseMapper.deleteBatchIds(list)));
    }

    /**
     * 根据 columnMap 条件，删除记录
     *
     * @param columnMap   表字段 map 对象
     * @param entityClass 实体类
     */
    public static <T> boolean removeByMap(Map<String, Object> columnMap, Class<T> entityClass) {
        return SqlHelper.execute(entityClass, baseMapper -> SqlHelper.retBool(baseMapper.deleteByMap(columnMap)));
    }

    /**
     * TableId 注解存在更新记录，否插入一条记录
     *
     * @param entity 实体对象
     */
    public static <T> boolean saveOrUpdate(T entity) {
        if (Objects.isNull(entity)) {
            return false;
        }
        Class<T> entityClass = getEntityClass(entity);
        TableInfo tableInfo = TableInfoHelper.getTableInfo(entityClass);
        Assert.notNull(tableInfo, "error: can not execute. because can not find cache of TableInfo for entity!");
        String keyProperty = tableInfo.getKeyProperty();
        Assert.notEmpty(keyProperty, "error: can not execute. because can not find column for id from entity!");
        Object idVal = tableInfo.getPropertyValue(entity, tableInfo.getKeyProperty());
        return StringUtils.checkValNull(idVal) || Objects.isNull(getById((Serializable) idVal, entityClass)) ? save(entity) : updateById(entity);
    }

    /**
     * 根据 ID 查询
     *
     * @param id          主键ID
     * @param entityClass 实体类
     */
    public static <T> T getById(Serializable id, Class<T> entityClass) {
        return SqlHelper.execute(entityClass, baseMapper -> baseMapper.selectById(id));
    }

    /**
     * 根据 Wrapper，查询一条记录 <br/>
     * <p>结果集，如果是多个会抛出异常，随机取一条加上限制条件 wrapper.last("LIMIT 1")</p>
     *
     * @param queryWrapper 实体对象封装操作类 {@link com.baomidou.mybatisplus.core.conditions.query.QueryWrapper}
     */
    public static <T> T getOne(AbstractWrapper<T, ?, ?> queryWrapper) {
        return getOne(queryWrapper, true);
    }

    /**
     * 根据 entity里不为空的字段，查询一条记录 <br/>
     * <p>结果集，如果是多个会抛出异常，随机取一条加上限制条件 wrapper.last("LIMIT 1")</p>
     *
     * @param entity 实体对象
     */
    public static <T> T getOne(T entity) {
        return getOne(Wrappers.lambdaQuery(entity), true);
    }

    /**
     * 根据 entity里不为空的字段，查询一条记录
     *
     * @param entity  实体对象
     * @param throwEx 有多个 result 是否抛出异常
     */
    public static <T> T getOne(T entity, boolean throwEx) {
        return getOne(Wrappers.lambdaQuery(entity), throwEx);
    }

    /**
     * 根据 Wrapper，查询一条记录
     *
     * @param queryWrapper 实体对象封装操作类 {@link com.baomidou.mybatisplus.core.conditions.query.QueryWrapper}
     * @param throwEx      有多个 result 是否抛出异常
     */
    public static <T> T getOne(AbstractWrapper<T, ?, ?> queryWrapper, boolean throwEx) {
        Class<T> entityClass = getEntityClass(queryWrapper);
        if (throwEx) {
            return SqlHelper.execute(entityClass, baseMapper -> baseMapper.selectOne(queryWrapper));
        }
        return SqlHelper.execute(entityClass, baseMapper -> SqlHelper.getObject(log, baseMapper.selectList(queryWrapper)));
    }

    /**
     * 查询（根据 columnMap 条件）
     *
     * @param columnMap   表字段 map 对象
     * @param entityClass 实体类
     */
    public static <T> List<T> listByMap(Map<String, Object> columnMap, Class<T> entityClass) {
        return SqlHelper.execute(entityClass, baseMapper -> baseMapper.selectByMap(columnMap));
    }

    /**
     * 查询（根据ID 批量查询）
     *
     * @param idList      主键ID列表
     * @param entityClass 实体类
     */
    public static <T> List<T> listByIds(Collection<? extends Serializable> idList, Class<T> entityClass) {
        return SqlHelper.execute(entityClass, baseMapper -> baseMapper.selectBatchIds(idList));
    }

    /**
     * 根据 Wrapper，查询一条记录
     *
     * @param queryWrapper 实体对象封装操作类 {@link com.baomidou.mybatisplus.core.conditions.query.QueryWrapper}
     */
    public static <T> Map<String, Object> getMap(AbstractWrapper<T, ?, ?> queryWrapper) {
        return SqlHelper.execute(getEntityClass(queryWrapper), baseMapper -> SqlHelper.getObject(log, baseMapper.selectMaps(queryWrapper)));
    }

    /**
     * 根据 entity不为空条件，查询一条记录
     *
     * @param entity 实体对象
     */
    public static <T> Map<String, Object> getMap(T entity) {
        return getMap(Wrappers.lambdaQuery(entity));
    }

    /**
     * 查询总记录数
     *
     * @param entityClass 实体类
     * @see Wrappers#emptyWrapper()
     */
    public static <T> long count(Class<T> entityClass) {
        return SqlHelper.execute(entityClass, baseMapper -> baseMapper.selectCount(null));
    }

    /**
     * 根据entity中不为空的数据查询记录数
     *
     * @param entity 实体类
     */
    public static <T> long count(T entity) {
        return count(Wrappers.lambdaQuery(entity));
    }

    /**
     * 根据 Wrapper 条件，查询总记录数
     *
     * @param queryWrapper 实体对象封装操作类 {@link com.baomidou.mybatisplus.core.conditions.query.QueryWrapper}
     */
    public static <T> long count(AbstractWrapper<T, ?, ?> queryWrapper) {
        return SqlHelper.execute(getEntityClass(queryWrapper), baseMapper -> baseMapper.selectCount(queryWrapper));
    }

    /**
     * 查询列表
     *
     * @param queryWrapper 实体对象封装操作类 {@link com.baomidou.mybatisplus.core.conditions.query.QueryWrapper}
     */
    public static <T> List<T> list(AbstractWrapper<T, ?, ?> queryWrapper) {
        return SqlHelper.execute(getEntityClass(queryWrapper), baseMapper -> baseMapper.selectList(queryWrapper));
    }

    /**
     * @param page         分页条件
     * @param queryWrapper 实体对象封装操作类 {@link com.baomidou.mybatisplus.core.conditions.query.QueryWrapper}
     * @param <T>          entity
     * @return 列表数据
     */
    public static <T> List<T> list(IPage<T> page, AbstractWrapper<T, ?, ?> queryWrapper) {
        return SqlHelper.execute(getEntityClass(queryWrapper), baseMapper -> baseMapper.selectList(page, queryWrapper));
    }


    /**
     * 查询所有
     *
     * @param entityClass 实体类
     * @see Wrappers#emptyWrapper()
     */
    public static <T> List<T> list(Class<T> entityClass) {
        return SqlHelper.execute(entityClass, baseMapper -> baseMapper.selectList(null));
    }

    /**
     * @param page        分页条件
     * @param entityClass 实体类
     * @param <T>         entity
     * @return 列表数据
     * @since 3.5.3.2
     */
    public static <T> List<T> list(IPage<T> page, Class<T> entityClass) {
        return SqlHelper.execute(entityClass, baseMapper -> baseMapper.selectList(page, null));
    }


    /**
     * 根据entity中不为空的字段进行查询
     *
     * @param entity 实体类
     * @see Wrappers#emptyWrapper()
     */
    public static <T> List<T> list(T entity) {
        return list(Wrappers.lambdaQuery(entity));
    }

    /**
     * 根据entity中不为空的字段进行查询
     *
     * @param page   分页条件
     * @param entity 实体类
     * @param <T>    entity
     * @return 列表数据
     * @since 3.5.3.2
     */
    public static <T> List<T> list(IPage<T> page, T entity) {
        return list(page, Wrappers.lambdaQuery(entity));
    }

    /**
     * 查询列表
     *
     * @param queryWrapper 实体对象封装操作类 {@link com.baomidou.mybatisplus.core.conditions.query.QueryWrapper}
     */
    public static <T> List<Map<String, Object>> listMaps(AbstractWrapper<T, ?, ?> queryWrapper) {
        return SqlHelper.execute(getEntityClass(queryWrapper), baseMapper -> baseMapper.selectMaps(queryWrapper));
    }

    /**
     * @since 3.5.3.2
     * @param page 分页参数
     * @param queryWrapper queryWrapper 实体对象封装操作类 {@link com.baomidou.mybatisplus.core.conditions.query.QueryWrapper}
     * @return 列表数据
     * @param <T> entity
     */
    public static <T> List<Map<String, Object>> listMaps(IPage<? extends Map<String, Object>> page, AbstractWrapper<T, ?, ?> queryWrapper) {
        return SqlHelper.execute(getEntityClass(queryWrapper), baseMapper -> baseMapper.selectMaps(page, queryWrapper));
    }

    /**
     * 查询所有列表
     *
     * @param entityClass 实体类
     * @see Wrappers#emptyWrapper()
     */
    public static <T> List<Map<String, Object>> listMaps(Class<T> entityClass) {
        return SqlHelper.execute(entityClass, baseMapper -> baseMapper.selectMaps(null));
    }

    /**
     * 分页查询列表
     *
     * @param page        分页条件
     * @param entityClass 实体类
     * @param <T>         entity
     * @return 列表数据
     * @since 3.5.3.2
     */
    public static <T> List<Map<String, Object>> listMaps(IPage<? extends Map<String, Object>> page, Class<T> entityClass) {
        return SqlHelper.execute(entityClass, baseMapper -> baseMapper.selectMaps(page, null));
    }


    /**
     * 根据entity不为空的条件查询列表
     *
     * @param entity 实体类
     */
    public static <T> List<Map<String, Object>> listMaps(T entity) {
        return listMaps(Wrappers.lambdaQuery(entity));
    }

    /**
     * 根据entity不为空的条件查询列表
     *
     * @param page   分页条件
     * @param entity entity
     * @param <T>    entity
     * @return 列表数据
     * @since 3.5.3.2
     */
    public static <T> List<Map<String, Object>> listMaps(IPage<? extends Map<String, Object>> page, T entity) {
        return listMaps(page, Wrappers.lambdaQuery(entity));
    }

    /**
     * 查询全部记录
     *
     * @param entityClass 实体类
     */
    public static <T> List<T> listObjs(Class<T> entityClass) {
        return listObjs(entityClass, i -> i);
    }

    /**
     * 根据 Wrapper 条件，查询全部记录
     *
     * @param queryWrapper 实体对象封装操作类 {@link com.baomidou.mybatisplus.core.conditions.query.QueryWrapper}
     */
    public static <E, T> List<E> listObjs(AbstractWrapper<T, ?, ?> queryWrapper) {
        return SqlHelper.execute(getEntityClass(queryWrapper), baseMapper -> baseMapper.selectObjs(queryWrapper));
    }

    /**
     * 根据 Wrapper 条件，查询全部记录
     *
     * @param queryWrapper 实体对象封装操作类 {@link com.baomidou.mybatisplus.core.conditions.query.QueryWrapper}
     * @param mapper       转换函数
     */
    public static <T, V> List<V> listObjs(AbstractWrapper<T, ?, ?> queryWrapper, SFunction<? super T, V> mapper) {
        return SqlHelper.execute(getEntityClass(queryWrapper), baseMapper -> baseMapper.selectList(queryWrapper).stream().map(mapper).collect(Collectors.toList()));
    }

    /**
     * 查询全部记录
     *
     * @param entityClass 实体类
     * @param mapper      转换函数
     */
    public static <T, V> List<V> listObjs(Class<T> entityClass, SFunction<? super T, V> mapper) {
        return SqlHelper.execute(entityClass, baseMapper -> baseMapper.selectList(null).stream().map(mapper).collect(Collectors.toList()));
    }

    /**
     * 无条件翻页查询
     *
     * @param page        翻页对象
     * @param entityClass 实体类
     * @see Wrappers#emptyWrapper()
     */
    public static <T, E extends IPage<Map<String, Object>>> E pageMaps(E page, Class<T> entityClass) {
        return SqlHelper.execute(entityClass, baseMapper -> baseMapper.selectMapsPage(page, null));
    }

    /**
     * 翻页查询
     *
     * @param page         翻页对象
     * @param queryWrapper 实体对象封装操作类 {@link com.baomidou.mybatisplus.core.conditions.query.QueryWrapper}
     */
    public static <T, E extends IPage<Map<String, Object>>> E pageMaps(E page, AbstractWrapper<T, ?, ?> queryWrapper) {
        return SqlHelper.execute(getEntityClass(queryWrapper), baseMapper -> baseMapper.selectMapsPage(page, queryWrapper));
    }

    /**
     * 无条件翻页查询
     *
     * @param page        翻页对象
     * @param entityClass 实体类
     * @see Wrappers#emptyWrapper()
     */
    public static <T> IPage<T> page(IPage<T> page, Class<T> entityClass) {
        return SqlHelper.execute(entityClass, baseMapper -> baseMapper.selectPage(page, null));
    }

    /**
     * 翻页查询
     *
     * @param page         翻页对象
     * @param queryWrapper 实体对象封装操作类 {@link com.baomidou.mybatisplus.core.conditions.query.QueryWrapper}
     */
    public static <T> IPage<T> page(IPage<T> page, AbstractWrapper<T, ?, ?> queryWrapper) {
        return SqlHelper.execute(getEntityClass(queryWrapper), baseMapper -> baseMapper.selectPage(page, queryWrapper));
    }

    /**
     * 链式查询 普通
     *
     * @return QueryWrapper 的包装类
     */
    public static <T> QueryChainWrapper<T> query(Class<T> entityClass) {
        return ChainWrappers.queryChain(entityClass);
    }

    /**
     * kt链式查询
     *
     * @return KtQueryWrapper 的包装类
     */
    public static <T> KtQueryChainWrapper<T> ktQuery(Class<T> entityClass) {
        return ChainWrappers.ktQueryChain(entityClass);
    }


    /**
     * 链式查询 lambda 式
     * <p>注意：不支持 Kotlin </p>
     *
     * @return LambdaQueryWrapper 的包装类
     */
    public static <T> LambdaQueryChainWrapper<T> lambdaQuery(Class<T> entityClass) {
        return ChainWrappers.lambdaQueryChain(entityClass);
    }

    /**
     * 链式更改 普通
     *
     * @return UpdateWrapper 的包装类
     */
    public static <T> UpdateChainWrapper<T> update(Class<T> entityClass) {
        return ChainWrappers.updateChain(entityClass);
    }

    /**
     * kt链式更改
     *
     * @return KtUpdateWrapper 的包装类
     */
    public static <T> KtUpdateChainWrapper<T> ktUpdate(Class<T> entityClass) {
        return ChainWrappers.ktUpdateChain(entityClass);
    }

    /**
     * 链式更改 lambda 式
     * <p>注意：不支持 Kotlin </p>
     *
     * @return LambdaUpdateWrapper 的包装类
     */
    public static <T> LambdaUpdateChainWrapper<T> lambdaUpdate(Class<T> entityClass) {
        return ChainWrappers.lambdaUpdateChain(entityClass);
    }

    /**
     * <p>
     * 根据updateWrapper尝试更新，否继续执行saveOrUpdate(T)方法
     * 此次修改主要是减少了此项业务代码的代码量（存在性验证之后的saveOrUpdate操作）
     * </p>
     *
     * @param entity 实体对象
     */
    public static <T> boolean saveOrUpdate(T entity, AbstractWrapper<T, ?, ?> updateWrapper) {
        return update(entity, updateWrapper) || saveOrUpdate(entity);
    }

    /**
     * 根据 Wrapper，查询一条记录
     *
     * @param queryWrapper 实体对象封装操作类 {@link com.baomidou.mybatisplus.core.conditions.query.QueryWrapper}
     * @param mapper       转换函数
     */
    public static <T, V> V getObj(AbstractWrapper<T, ?, ?> queryWrapper, SFunction<? super T, V> mapper) {
        return SqlHelper.execute(getEntityClass(queryWrapper), baseMapper -> mapper.apply(baseMapper.selectOne(queryWrapper)));
    }

    /**
     * 从集合中获取实体类型
     *
     * @param entityList 实体集合
     * @param <T>        实体类型
     * @return 实体类型
     */
    protected static <T> Class<T> getEntityClass(Collection<T> entityList) {
        Class<T> entityClass = null;
        for (T entity : entityList) {
            if (entity != null && entity.getClass() != null) {
                entityClass = getEntityClass(entity);
                break;
            }
        }
        Assert.notNull(entityClass, "error: can not get entityClass from entityList");
        return entityClass;
    }

    /**
     * 从wrapper中尝试获取实体类型
     *
     * @param queryWrapper 条件构造器
     * @param <T>          实体类型
     * @return 实体类型
     */
    protected static <T> Class<T> getEntityClass(AbstractWrapper<T, ?, ?> queryWrapper) {
        Class<T> entityClass = queryWrapper.getEntityClass();
        if (entityClass == null) {
            T entity = queryWrapper.getEntity();
            if (entity != null) {
                entityClass = getEntityClass(entity);
            }
        }
        Assert.notNull(entityClass, "error: can not get entityClass from wrapper");
        return entityClass;
    }

    /**
     * 从entity中尝试获取实体类型
     *
     * @param entity 实体
     * @param <T>    实体类型
     * @return 实体类型
     */
    @SuppressWarnings("unchecked")
    protected static <T> Class<T> getEntityClass(T entity) {
        return (Class<T>) entity.getClass();
    }


    /**
     * 获取表信息，获取不到报错提示
     *
     * @param entityClass 实体类
     * @param <T>         实体类型
     * @return 对应表信息
     */
    protected static <T> TableInfo getTableInfo(Class<T> entityClass) {
        return Optional.ofNullable(TableInfoHelper.getTableInfo(entityClass)).orElseThrow(() -> ExceptionUtils.mpe("error: can not find TableInfo from Class: \"%s\".", entityClass.getName()));
    }
}
```

示例：

```Java
@Test
void testDbGet() {
    User user = Db.getById(1L, User.class);
    System.out.println(user);
}

@Test
void testDbList() {
    // 利用Db实现复杂条件查询
    List<User> list = Db.lambdaQuery(User.class)
            .like(User::getUsername, "o")
            .ge(User::getBalance, 1000)
            .list();
    list.forEach(System.out::println);
}

@Test
void testDbUpdate() {
    Db.lambdaUpdate(User.class)
            .set(User::getBalance, 2000)
            .eq(User::getUsername, "Rose");
}
```



需求：改造根据 id 查询用户接口，查询用户的同时返回用户收获地址列表：

**UserVO：**

```java
/**
 * 用户表VO
 * @author lixuan
 * @Date 2024/8/7 17:33
 */
@Data
@EqualsAndHashCode(callSuper = true)
public class UserVO extends UserEntity {

    @Serial
    private static final long serialVersionUID = 1L;

    @Schema(description = "地址列表")
    private List<AddressVO> addressList;

}
```

添加一个地址列表的属性

**UserController：**

```java
/**
 * 查询用户并且对应其地址足迹
 */
@GetMapping("/getUserAndAddress/{id}")
@Operation(summary = "查询用户并且对应其地址足迹 getUserAndAddress/{id}")
public UserVO getUserAndAddress(@Parameter(description = "用户ID") @PathVariable("id") Long id) {
    //获取用户
    UserEntity userEntity = userService.getById(id);
    if (userEntity == null || userEntity.getStatus() == UserStatus.FREEZE) {
        throw new RuntimeException("用户状态异常！！");
    }
    //转换Vo
    UserVO userVO = BeanUtil.copyProperties(userEntity, UserVO.class);
    //获取地址列表
    List<AddressEntity> addressEntityList = addressService.list(Wrappers.lambdaQuery(AddressEntity.class)
            .eq(AddressEntity::getUserId, id));
    //转换列表VO
    if (CollUtil.isNotEmpty(addressEntityList)) {
        List<AddressVO> addressVOList = BeanUtil.copyToList(addressEntityList, AddressVO.class);
        userVO.setAddressList(addressVOList);
    }
    return userVO;
}
```

需求：根据id批量查询用户，并查询出用户对应的所有地址

```java
/**
 * 根据ids批量查询
 */
@GetMapping("/getUserByIds")
@Operation(summary = "根据ids批量查询 getUserByIds")
public List<UserVO> getUserByIds(@RequestParam List<Long> ids) {
    //1、查询用户
    List<UserEntity> userEntityList = userService.listByIds(ids);
    if (CollUtil.isEmpty(userEntityList)) {
        return Collections.emptyList();
    }
    //2查询地址列表
    List<AddressEntity> addressEntityList = addressService.list(Wrappers.lambdaQuery(AddressEntity.class)
            .in(AddressEntity::getUserId, ids));
    //转为Vo列表
    List<UserVO> userVOList = BeanUtil.copyToList(userEntityList, UserVO.class);
    //根据UserId转为Map
    Map<Long, List<AddressEntity>> addressEntityMap = addressEntityList.stream()
            .collect(Collectors.groupingBy(AddressEntity::getUserId));
    userVOList.forEach(userVO -> {
        if (userVO.getStatus() == UserStatus.FREEZE) {
            log.error("用户{}状态异常！！", userVO.getUsername());
        }

        //1、获取对应地址列表
        Optional.ofNullable(addressEntityMap.get(userVO.getId()))
                .ifPresent(addressEntities -> {
                    //2、转换为Vo地址列表
                    List<AddressVO> addressVOList = BeanUtil.copyToList(addressEntities, AddressVO.class);
                    //3、注入Vo
                    userVO.setAddressList(addressVOList);
                });
    });
    return userVOList;
}
```



## Ⅲ 逻辑删除

对于一些比较重要的数据，我们往往会采用逻辑删除的方式，而不是直接将其冲数据库中删除。

- 在表中添加一个字段标记数据是否被删除
- 当删除数据时把标记置为true
- 查询时过滤掉标记为true的数据

**MybatisPlus** 就添加了对逻辑删除的支持：

`注意，只有MybatisPlus生成的SQL语句才支持自动的逻辑删除，自定义SQL需要自己手动处理逻辑删除。`

例如，给 **adress** 表添加逻辑删除字段：

```SQL
alter table address add deleted bit default b'0' null comment '逻辑删除';
```

**AdressEntity：**

```java
/**
 * 地址表
 * @author lixuan
 * @TableName address
 */
@Data
@AllArgsConstructor
@NoArgsConstructor
@TableName(value ="address")
@Schema(description = "地址表")
public class AddressEntity implements Serializable {
    /**
     * 
     */
    @Schema(description = "id")
    @TableId(value = "id", type = IdType.AUTO)
    private Long id;

    /**
     * 用户ID
     */
    @Schema(description = "用户ID")
    @TableField(value = "user_id")
    private Long userId;

    /**
     * 省
     */
    @Schema(description = "省")
    @TableField(value = "province")
    private String province;

    /**
     * 市
     */
    @Schema(description = "市")
    @TableField(value = "city")
    private String city;

    /**
     * 县/区
     */
    @Schema(description = "县/区")
    @TableField(value = "town")
    private String town;

    /**
     * 手机
     */
    @Schema(description = "手机")
    @TableField(value = "mobile")
    private String mobile;

    /**
     * 详细地址
     */
    @Schema(description = "详细地址")
    @TableField(value = "street")
    private String street;

    /**
     * 联系人
     */
    @Schema(description = "联系人")
    @TableField(value = "contact")
    private String contact;

    /**
     * 是否是默认 1默认 0否
     */
    @Schema(description = "是否是默认 1默认 0否")
    @TableField(value = "is_default")
    private Boolean isDefault;

    /**
     * 备注
     */
    @Schema(description = "备注")
    @TableField(value = "notes")
    private String notes;

    /**
     * 逻辑删除
     */
    @Schema(description = "逻辑删除")
    @TableField(value = "deleted")
    private Boolean deleted;

    @Serial
    @TableField(exist = false)
    private static final long serialVersionUID = 1L;
}
```

**application.yml：**

```YAML
mybatis-plus:
  global-config:
    db-config:
      logic-delete-field: deleted # 全局逻辑删除的实体字段名(since 3.3.0,配置后可以忽略不配置步骤2)
      logic-delete-value: 1 # 逻辑已删除值(默认为 1)
      logic-not-delete-value: 0 # 逻辑未删除值(默认为 0)
```

方法与普通的方法一样，但是底层的逻辑已经改变了：

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v22.png)

查询：

```Java
@Test
void testQuery() {
    List<Address> list = addressService.list();
    list.forEach(System.out::println);
}
```

会发现 **id** 为59的确实没有查询出来，而且 **SQL** 中也对逻辑删除字段做了判断：

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v23.png)

综上， 开启了逻辑删除功能以后，我们就可以像普通删除一样做CRUD，基本不用考虑代码逻辑问题。还是非常方便的。

> **注意**： 逻辑删除本身也有自己的问题，比如：
>
> - 会导致数据库表垃圾数据越来越多，从而影响查询效率
> - SQL中全都需要对逻辑删除字段做判断，影响查询效率



## Ⅳ 通用枚举

**UserEntity** 中有一个用户状态

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v24.png)

像这种字段，我们一般会定义一个枚举，做业务判断的时候，就可以直接基于枚举比较，但是我们数据库采用的是 **int** 型，对应的 **PO** 也是一个 **Integer** 。因此业务操作时必须手动转换枚举和 **Integer** 。

但是 **MybatisPlus** 提供了一个处理枚举类型的类型转换器，可以帮我们把`枚举类型和数据库类型自动转换`。

### ① 定义枚举

定义一个用户状态枚举：

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v25.png)

代码如下：

```java
@Getter
public enum UserStatus {

    /**
     * 用户账号状态
     */
    NORMAL(1, "正常"),
    FREEZE(2, "冻结");

    @EnumValue
    private final int value;
    /**
     * JSON 响应时返回的属性值
     */
    @JsonValue
    private final String desc;

    UserStatus(int value, String desc) {
        this.value = value;
        this.desc = desc;
    }
}
```

然后将 `UserEntity` 类中的 `status` 字段改为 `UserStatus` 类型：

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v26.png)

当然，要让 `MybatisPlus` 处理枚举与数据库自动类型转换，我们必须要告诉 `MybatisPlus` ，枚举中的哪个字段值作为数据库值。

`MybatisPlus` 提供了 `@EnumValue` 来标记枚举属性

### ② 配置枚举处理器

在 **application.yml** 中添加配置：

```YAML
mybatis-plus:
  configuration:
    default-enum-type-handler: com.baomidou.mybatisplus.core.handlers.MybatisEnumTypeHandler
```

测试：

```java
/**
 * 枚举处理测试
 */
@Test
void testService() {
    List<UserEntity> list = userService.list();
    list.forEach(System.out::println);
}
```

最终，查询出的`User`类的`status`字段会是枚举类型：

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v27.png)

同时，为了使页面查询结果也是枚举格式，我们需要修改UserVO中的status属性

并且，在UserStatus枚举中通过`@JsonValue`注解标记JSON序列化时展示的字段：

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v28.png)

最后，在页面查询，结果如下：

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v29.png)



## Ⅴ JSON 类型处理器

数据库的user表中有一个`info`字段，是 **JSON** 类型：

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v30.png)

格式：

```JSON
{"age": 20, "intro": "佛系青年", "gender": "male"}
```

而目前`UserEntity`实体类中却是`String`类型：

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v31.png)

这样一来，我们要读取info中的属性时就非常不方便。如果要方便获取，info的类型最好是一个`Map`或者实体类。

而一旦我们把`info`改为`对象`类型，就需要在写入数据库时手动转为`String`，再读取数据库时，手动转换为`对象`，这会非常麻烦。

因此MybatisPlus提供了很多特殊类型字段的类型处理器，解决特殊字段类型与数据库类型转换的问题。例如处理JSON就可以使用`JacksonTypeHandler`处理器。

### ① 定义实体

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v32.png)

代码如下：

```java
/**
 * Json UserInfo
 * @author lixuan
 * @Date 2024/8/9 9:20
 */
@Data
@NoArgsConstructor
@AllArgsConstructor(staticName = "of")
public class UserInfo {
    private Integer age;
    private String intro;
    private String gender;
}
```

### ② 使用类型处理器	

将 UserEntity 类的 info 字段修改为 UserInfo 类型，并声明类型处理器：

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v33.png)



# 插件功能

MybatisPlus提供了很多的插件功能，进一步拓展其功能。目前已有的插件有：

- `PaginationInnerInterceptor`：自动分页
- `TenantLineInnerInterceptor`：多租户
- `DynamicTableNameInnerInterceptor`：动态表名
- `OptimisticLockerInnerInterceptor`：乐观锁
- `IllegalSQLInnerInterceptor`：sql 性能规范
- `BlockAttackInnerInterceptor`：防止全表更新与删除

> **注意：** 使用多个分页插件的时候需要注意插件定义顺序，建议使用顺序如下：
>
> - 多租户,动态表名
> - 分页,乐观锁
> - sql 性能规范,防止全表更新与删除



## Ⅰ分页插件

在未引入分页插件的情况下，`MybatisPlus`是不支持分页功能的，`IService`和`BaseMapper`中的分页方法都无法正常起效。 所以，我们必须配置分页插件。

### ① 配置分页插件

在 **config** 下配置分页插件

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v34.png)

代码如下：

```java
/**
 * 分页拦截器
 * @author lixuan
 * @Date 2024/8/8 9:36
 */
@Configuration
public class MybatisPlusConfig {
    /**
     * 定义一个mybatisPlus的拦截器 再 add一个分页拦截器
     */
    @Bean
    public MybatisPlusInterceptor mybatisPlusInterceptor(){
        //1.初始化核心插件
        MybatisPlusInterceptor mybatisPlusInterceptor = new MybatisPlusInterceptor();
        //2.添加分页插件
        mybatisPlusInterceptor.addInnerInterceptor(new PaginationInnerInterceptor());
        return mybatisPlusInterceptor;
    }

}
```

### ② 分页 API

```java
/**
 * 分页测试
 */
@Test
void testPageQuery() {
    // 1.分页查询，new Page()的两个参数分别是：页码、每页大小
    int current = 1;
    int size = 2;
    Page<UserEntity> page = Page.of(current, size);
    // 1.2、排序
    page.addOrder(OrderItem.asc("balance"));
    page.addOrder(OrderItem.desc("id"));
    Page<UserEntity> p = userService.page(page);
    // 2.总条数
    System.out.println("total = " + p.getTotal());
    // 3.总页数
    System.out.println("pages = " + p.getPages());

    // 4.数据
    List<UserEntity> records = p.getRecords();
    records.forEach(System.out::println);
}
```

![AbstractWrapper](images/frameworks/Java/mybatisplus/a/v35.png)

这里用到了分页参数，**Page** ，即可以支持分页参数，也可以支持排序参数。常见的 **API** 如下：

```Java
int pageNo = 1, pageSize = 5;
// 分页参数
Page<User> page = Page.of(pageNo, pageSize);
// 排序参数, 通过OrderItem来指定
page.addOrder(new OrderItem("balance", false));

userService.page(page);
```



## Ⅱ 通用分页实体

现在要实现一个用户分页查询的接口，接口规范如下：

<table border="1" cellpadding="10" cellspacing="0" style="border-collapse: collapse; width: 100%; text-align: left;">
  <thead>
    <tr>
      <th style="background-color: #e0f7fa; color: #00796b;">参数</th>
      <th style="background-color: #e0f7fa; color: #00796b;">说明</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>请求方式</td>
      <td>GET</td>
    </tr>
    <tr>
      <td>请求路径</td>
      <td>/users/page</td>
    </tr>
    <tr>
      <td>请求参数</td>
      <td>
        <pre style="background-color: #050917; border: 1px solid rgb(5,9,23); border-radius: 4px; padding: 10px;">
{
  "pageNo": 1,
  "pageSize": 5,
  "sortBy": "balance",
  "isAsc": false,
  "name": "o",
  "status": 1
}
        </pre>
      </td>
    </tr>
    <tr>
      <td>返回值</td>
      <td>
        <pre style="background-color: #050917; border: 1px solid rgb(5,9,23); border-radius: 4px; padding: 10px;">
{
  "total": 100006,
  "pages": 50003,
  "list": [
    {
      "id": 1685100878975279298,
      "username": "user_9****",
      "info": {
        "age": 24,
        "intro": "英文老师",
        "gender": "female"
      },
      "status": "正常",
      "balance": 2000
    }
  ]
}
        </pre>
      </td>
    </tr>
    <tr>
      <td>特殊说明</td>
      <td>如果排序字段为空，默认按照更新时间排序；如果排序字段不为空，则按照排序字段排序。</td>
    </tr>
  </tbody>
</table>

这里需要定义3个实体：

- `UserQuery`：分页查询条件的实体，包含分页、排序参数、过滤条件
- `PageDTO`：分页结果实体，包含总条数、总页数、当前页数据
- `UserVO`：用户页面视图实体

### ① 实体

**UserQuery：**

```java
@Data
@EqualsAndHashCode(callSuper = true)
@Schema(description = "用户查询条件实体")
public class UserQuery extends PageQuery {
    @Schema(description = "用户名关键字")
    private String name;
    @Schema(description = "用户状态：1-正常，2-冻结")
    private Integer status;
    @Schema(description = "余额最小值")
    private Integer minBalance;
    @Schema(description = "余额最大值")
    private Integer maxBalance;
}
```

**PageQuery：**

```java
@Data
@Schema(description = "分页查询实体")
public class PageQuery {
    @Schema(description = "页码")
    private Long pageNo;
    @Schema(description = "页码")
    private Long pageSize;
    @Schema(description = "排序字段")
    private String sortBy;
    @Schema(description = "是否升序")
    private Boolean isAsc;

    public <T> Page<T> toMpPage(OrderItem... orders){
        // 1.分页条件
        Page<T> p = Page.of(pageNo, pageSize);
        // 2.排序条件
        // 2.1.先看前端有没有传排序字段
        if (sortBy != null) {
            p.addOrder(isAsc!= null&& isAsc ? OrderItem.asc(sortBy) : OrderItem.desc(sortBy));
            return p;
        }
        // 2.2.再看有没有手动指定排序字段
        if(orders != null){
            p.addOrder(orders);
        }
        return p;
    }

    public <T> Page<T> toMpPage(String defaultSortBy, boolean isAsc){
        return this.toMpPage(isAsc ? OrderItem.asc(defaultSortBy) : OrderItem.desc(defaultSortBy));
    }

    public <T> Page<T> toMpPageDefaultSortByCreateTimeDesc() {
        return toMpPage("create_time", false);
    }

    public <T> Page<T> toMpPageDefaultSortByUpdateTimeDesc() {
        return toMpPage("update_time", false);
    }
}
```

`PageQuery`是前端提交的查询参数，一般包含四个属性：

- `pageNo`：页码
- `pageSize`：每页数据条数
- `sortBy`：排序字段
- `isAsc`：是否升序

**PageDTO：**

```java
@Data
@Schema(description = "分页结果")
@AllArgsConstructor
@NoArgsConstructor
public class PageDTO<T> {
    @Schema(description = "总条数")
    private Long total;
    @Schema(description = "总页数")
    private Long pages;
    @Schema(description = "集合")
    private List<T> list;

    /**
     * 返回空分页结果
     * @param p MybatisPlus的分页结果
     * @param <V> 目标VO类型
     * @param <P> 原始PO类型
     * @return VO的分页对象
     */
    public static <V, P> PageDTO<V> empty(Page<P> p){
        return new PageDTO<>(p.getTotal(), p.getPages(), Collections.emptyList());
    }

    /**
     * 将MybatisPlus分页结果转为 VO分页结果
     * @param p MybatisPlus的分页结果
     * @param voClass 目标VO类型的字节码
     * @param <V> 目标VO类型
     * @param <P> 原始PO类型
     * @return VO的分页对象
     */
    public static <V, P> PageDTO<V> of(Page<P> p, Class<V> voClass) {
        // 1.非空校验
        List<P> records = p.getRecords();
        if (records == null || records.size() <= 0) {
            // 无数据，返回空结果
            return empty(p);
        }
        // 2.数据转换
        List<V> vos = BeanUtil.copyToList(records, voClass);
        // 3.封装返回
        return new PageDTO<>(p.getTotal(), p.getPages(), vos);
    }

    /**
     * 将MybatisPlus分页结果转为 VO分页结果，允许用户自定义PO到VO的转换方式
     * @param p MybatisPlus的分页结果
     * @param convertor PO到VO的转换函数
     * @param <V> 目标VO类型
     * @param <P> 原始PO类型
     * @return VO的分页对象
     */
    public static <V, P> PageDTO<V> of(Page<P> p, Function<P, V> convertor) {
        // 1.非空校验
        List<P> records = p.getRecords();
        if (records == null || records.size() <= 0) {
            // 无数据，返回空结果
            return empty(p);
        }
        // 2.数据转换
        List<V> vos = records.stream().map(convertor).collect(Collectors.toList());
        // 3.封装返回
        return new PageDTO<>(p.getTotal(), p.getPages(), vos);
    }
}
```

### ② 开发接口

```java
/**
 * 分页查询 page
 */
@GetMapping("/page")
@Operation(summary = "分页查询 page")
public PageDTO<UserVO> queryUsersPage(@ParameterObject UserQuery query){
    log.info("queryUsersPage ===> {}", query);
    Page<UserEntity> userEntityPage = userService.page(new Page<UserEntity>(query.getPageNo(), query.getPageSize())
                    .addOrder(ObjectUtil.isEmpty(query.getSortBy()) ?
                            OrderItem.desc("update_time") :
                            (query.getIsAsc() != null && query.getIsAsc() ?
                                    OrderItem.asc(query.getSortBy()) :
                                    OrderItem.desc(query.getSortBy()))),
            Wrappers.lambdaQuery(UserEntity.class)
                    .like(StrUtil.isNotBlank(query.getName()), UserEntity::getUsername, query.getName())
                    .between(query.getMinBalance() != null && query.getMaxBalance() != null, UserEntity::getBalance, query.getMinBalance(), query.getMaxBalance()));
    System.out.println("userEntityPage = " + userEntityPage.getRecords());
    //转换为Vo
    List<UserVO> userVOList = BeanUtil.copyToList(userEntityPage.getRecords(), UserVO.class);
    PageDTO<UserVO> userVoPageDTO = new PageDTO<>(userEntityPage.getCurrent(), userEntityPage.getSize(), userVOList);
    userVoPageDTO.setTotal(userEntityPage.getTotal());
    System.out.println("userVoPageDTO = " + userVoPageDTO.getPages());
    return userService.queryUsersPage(query);
}
```

