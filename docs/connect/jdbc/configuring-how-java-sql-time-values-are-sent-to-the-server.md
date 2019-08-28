---
title: Настройка способа отправки значений java.sql.Time на сервер | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 07eb00dd-621a-46f9-a5a5-8cab4d6058b5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8fe6969d51834d0798a530b9cc9926af1b27fec2
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028228"
---
# <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>Настройка способа отправки значений java.sql.Time на сервер
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Если для задания параметра используется объект java.sql.Time или тип JDBC java.sql.Types.TIME, то можно настроить порядок отправки значения java.sql.Time на сервер: в виде типа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **time** или в виде типа **datetime**.  
  
 Этот сценарий применяется в случае использования одного из следующих методов:  
  
-   [SQLServerCallableStatement.registerOutParameter(int, int)](../../connect/jdbc/reference/registeroutparameter-method-int-int.md)  
  
-   [SQLServerCallableStatement.registerOutParameter(int, int, int)](../../connect/jdbc/reference/registeroutparameter-method-int-int-int.md)  
  
-   [SQLServerCallableStatement.setTime](../../connect/jdbc/reference/settime-method-sqlservercallablestatement.md)  
  
-   [SQLServerPreparedStatement.setTime](../../connect/jdbc/reference/settime-method-sqlserverpreparedstatement.md)  
  
-   [SQLServerCallableStatement.setObject](../../connect/jdbc/reference/setobject-method-sqlservercallablestatement.md)  
  
-   [SQLServerPreparedStatement.setObject](../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)  
  
 Порядок отправки значения java.sql.Time можно настроить с помощью свойства соединения **sendTimeAsDatetime**. Дополнительные сведения: [Задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Значение свойства соединения **sendTimeAsDatetime** можно изменить программным образом с помощью [SQLServerDataSource.setSendTimeAsDatetime](../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Более ранние версии, чем, не поддерживают тип данных **time**, поэтому приложения, использующие Java.SQL.Time, обычно хранят значения Java.SQL.time как типы данных **DateTime** или **smalldatetime**. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
 Если вы хотите использовать типы данных **DateTime** и **smalldatetime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при работе со значениями Java. SQL. Time, следует задать для свойства соединения **сендтимеасдатетиме** **значение true**. Если вы хотите использовать тип данных **time** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при работе со значениями Java. SQL. Time, следует задать для свойства соединения **сендтимеасдатетиме** **значение false**.  
  
 Учтите, что если значения java.sql.Time передаются в параметр, тип данных которого также поддерживает хранение дат, то даты по умолчанию различаются в зависимости от типа отправки значения java.sql.Time — **datetime** (1 января 1970 г.) или **time** (1 января 1900 г.). Дополнительные сведения о преобразовании данных при отправке на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Использование даты и времени](https://go.microsoft.com/fwlink/?LinkID=145211).  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвере JDBC 3,0 по умолчанию **сендтимеасдатетиме** имеет значение true. В следующей версии свойство соединения **sendTimeAsDatetime** может иметь значение false по умолчанию.  
  
 Чтобы гарантировать, что приложение будет работать ожидаемым образом независимо от значения по умолчанию для свойства соединения **sendTimeAsDatetime**, можно выполнить следующие действия.  
  
-   Использовать java.sql.Time при работе с типом данных **time**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Используйте Java. SQL. timestamp при работе с типами данных **DateTime**, **smalldatetime**и **datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
Сендтимеасдатетиме должен иметь значение false для зашифрованных столбцов, так как зашифрованные столбцы не поддерживают преобразование из времени в DateTime. Начиная с Microsoft JDBC Driver 6,0 для SQL Server класс SQLServerConnection содержит два следующих метода для задания или получения значения свойства Сендтимеасдатетиме.

```java
  public boolean getSendTimeAsDatetime()
  public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)
```
  
## <a name="see-also"></a>См. также раздел
 [Основные сведения о типах данных JDBC Driver](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
