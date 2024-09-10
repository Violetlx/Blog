---
title: MybatisPlus
tags:
  - 工具
categories:
  - 开发框架
  - MyBatisPlus
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
