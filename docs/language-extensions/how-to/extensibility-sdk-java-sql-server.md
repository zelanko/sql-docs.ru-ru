---
title: Пакет Microsoft Extensibility SDK для Java
description: Узнайте, как реализовать программу Java для SQL Server с помощью пакета Microsoft Extensibility SDK для Java.
ms.prod: sql
ms.technology: language-extensions
ms.date: 11/05/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 011d8ba2e9c92d0df6fe2956c190f61934948f54
ms.sourcegitcommit: 82b92f73ca32fc28e1948aab70f37f0efdb54e39
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94870141"
---
# <a name="microsoft-extensibility-sdk-for-java-for-sql-server"></a>Пакет SDK Майкрософт для расширения возможностей Java в SQL Server
[!INCLUDE [SQL Server 2019 and later](../../includes/applies-to-version/sqlserver2019.md)]

Узнайте, как реализовать программу Java для SQL Server с помощью пакета Microsoft Extensibility SDK для Java. Пакет SDK — это интерфейс для расширения языка Java, который используется для обмена данными с SQL Server и выполнения кода Java из SQL Server.

Пакет SDK устанавливается как часть SQL Server 2019 релиза-кандидата 1 как в Windows, так и в Linux:

+ Путь установки по умолчанию в Windows: **[домашний каталог установки экземпляра]\MSSQL\Binn\mssql-java-lang-extension.jar**
+ Путь установки по умолчанию в Linux: **/opt/mssql/lib/mssql-java-lang-extension.jar**

Это открытый код, который можно найти в [репозитории расширений языка SQL Server в GitHub](https://github.com/microsoft/sql-server-language-extensions).

## <a name="implementation-requirements"></a>Требования к реализации

Интерфейс SDK определяет набор требований, которые должны быть выполнены для того, чтобы SQL Server мог взаимодействовать со средой выполнения Java. Чтобы использовать пакет SDK, необходимо выполнить некоторые правила реализации в основном классе. После этого SQL Server сможет выполнять определенный метод в классе Java и обмениваться данными с помощью расширения языка Java.

Пример использования пакета SDK см. здесь: [Учебник. Поиск строки с использованием регулярных выражений (regex) в Java](../tutorials/search-for-string-using-regular-expressions-in-java.md).

## <a name="sdk-classes"></a>Классы SDK

Пакет SDK состоит из трех классов.

Два абстрактных класса определяют интерфейс, который расширение Java использует для обмена данными с SQL Server:

- **AbstractSqlServerExtensionExecutor**
- **AbstractSqlServerExtensionDataset**

Третий класс является вспомогательным и содержит реализацию объекта набора данных. Этот класс необязателен, но упрощает начало работы. Вместо него можно использовать собственную реализацию такого класса.

- **PrimitiveDataset**

Ниже вы найдете описания каждого класса в пакете SDK. Исходный код классов в пакете SDK доступен в [репозитории расширений языка SQL Server в GitHub](https://github.com/microsoft/sql-server-language-extensions/tree/master/language-extensions/java/sdk).

### <a name="class-abstractsqlserverextensionexecutor"></a>Класс: AbstractSqlServerExtensionExecutor

Абстрактный класс **AbstractSqlServerExtensionExecutor** содержит интерфейс, который используется расширением языка Java для SQL Server для выполнения кода Java.

Основной класс Java должен наследовать этому классу. Наследование этому классу означает наличие в классе определенных методов, которые должны быть реализованы в вашем собственном классе.

Для наследования этому абстрактному классу можно расширить имя этого абстрактного класса в объявлении класса:

```java
public class <MyClass> extends AbstractSqlServerExtensionExecutor {}
```

Ваш основной класс должен, как минимум, реализовывать метод execute(...).

#### <a name="method-execute"></a>Метод execute

Метод execute — это метод, который вызывается из SQL Server через расширение языка Java для вызова кода Java из SQL Server. Это ключевой метод. В него вы будете включать основные операции, которые хотите выполнять из SQL Server.

Чтобы передать аргументы метода в Java из SQL Server, используйте параметр `@param` в `sp_execute_external_script`. Так метод **execute** принимает свои аргументы.

```java
public AbstractSqlServerExtensionDataset execute(AbstractSqlServerExtensionDataset input, LinkedHashMap<String, Object> params)  {}
```

#### <a name="method-init"></a>Метод init

Метод init выполняется после метода constructor и перед методом execute. В этом методе можно выполнять любые операции, которые необходимо выполнить перед методом execute(...).

```java
public void init(String sessionId, int taskId, int numtask) {}
```

### <a name="class-abstractsqlserverextensiondataset"></a>Класс: AbstractSqlServerExtensionDataset

Абстрактный класс **AbstractSqlServerExtensionDataset** содержит интерфейс для обработки входных и выходных данных, используемых расширением Java.


### <a name="class-primitivedataset"></a>Класс: PrimitiveDataset

Класс **PrimitiveDataset** является реализацией класса **AbstractSqlServerExtensionDataset**, в которой простые типы хранятся как массивы примитивов.

Он предоставляется в пакете SDK как дополнительный, вспомогательный класс. Если этот класс не используется, реализуйте собственный класс, наследующий классу **AbstractSqlServerExtensionDataset**.  

## <a name="next-steps"></a>Дальнейшие шаги

+ [Руководство. Поиск строки с использованием регулярных выражений (regex) в Java](../tutorials/search-for-string-using-regular-expressions-in-java.md)
+ [Как вызвать код Java в SQL Server](call-java-from-sql.md)
