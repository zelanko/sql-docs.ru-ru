---
title: Настройка способа отправки значений java.sql.Time на сервер | Документы Майкрософт
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 07eb00dd-621a-46f9-a5a5-8cab4d6058b5
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 49925570b878bc442e10ab89e3eb9ef6694232d5
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66797523"
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
  
 Версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] более ранней, чем [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] не поддерживают **время** значения типа данных, поэтому приложения, использующие java.sql.Time, обычно сохраняют java.sql.Time **datetime** или **smalldatetime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных.  
  
 Если вы хотите использовать **datetime** и **smalldatetime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных при работе со значениями java.sql.Time, следует задать **sendTimeAsDatetime** Свойства соединения **true**. Если вы хотите использовать **время** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типу данных, при работе со значениями java.sql.Time, следует задать **sendTimeAsDatetime** свойства соединения **false**.  
  
 Учтите, что если значения java.sql.Time передаются в параметр, тип данных которого также поддерживает хранение дат, то даты по умолчанию различаются в зависимости от типа отправки значения java.sql.Time — **datetime** (1 января 1970 г.) или **time** (1 января 1900 г.). Дополнительные сведения о преобразовании данных при отправке на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в разделе [Использование даты и времени](https://go.microsoft.com/fwlink/?LinkID=145211).  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 3.0 драйвера JDBC **sendTimeAsDatetime** по умолчанию имеет значение true. В следующей версии свойство соединения **sendTimeAsDatetime** может иметь значение false по умолчанию.  
  
 Чтобы гарантировать, что приложение будет работать ожидаемым образом независимо от значения по умолчанию для свойства соединения **sendTimeAsDatetime**, можно выполнить следующие действия.  
  
-   Использовать java.sql.Time при работе с типом данных **time**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Использовать java.sql.Timestamp при работе с **datetime**, **smalldatetime**, и **datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных.  
  
SendTimeAsDatetime должно иметь значение false, если для зашифрованных столбцов, так как зашифрованные столбцы не поддерживает преобразование из времени в datetime. Класс SQLServerConnection, начиная с Microsoft JDBC Driver 6.0 для SQL Server, имеет следующие два метода set или get значение свойства sendTimeAsDatetime.

```java
  public boolean getSendTimeAsDatetime()
  public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)
```
  
## <a name="see-also"></a>См. также:  
 [Основные сведения о типах данных драйвера JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
