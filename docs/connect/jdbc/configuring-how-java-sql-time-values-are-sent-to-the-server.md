---
title: Настройка способа отправки значений java.sql.Time сервер | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 07eb00dd-621a-46f9-a5a5-8cab4d6058b5
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e2e91550767715616599c2720c99b864363a185
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32831969"
---
# <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>Настройка способа отправки значений java.sql.Time на сервер
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Если для задания параметра используется объект java.sql.Time или тип JDBC java.sql.Types.TIME, можно настроить как значения java.sql.Time отправляется на сервер; либо как [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **время** типа или как **datetime** типа.  
  
 Этот сценарий применяется в случае использования одного из следующих методов:  
  
-   [SQLServerCallableStatement.registerOutParameter (int, int)](../../connect/jdbc/reference/registeroutparameter-method-int-int.md)  
  
-   [SQLServerCallableStatement.registerOutParameter (int, int, int)](../../connect/jdbc/reference/registeroutparameter-method-int-int-int.md)  
  
-   [SQLServerCallableStatement.setTime](../../connect/jdbc/reference/settime-method-sqlservercallablestatement.md)  
  
-   [SQLServerPreparedStatement.setTime](../../connect/jdbc/reference/settime-method-sqlserverpreparedstatement.md)  
  
-   [SQLServerCallableStatement.setObject](../../connect/jdbc/reference/setobject-method-sqlservercallablestatement.md)  
  
-   [SQLServerPreparedStatement.setObject](../../connect/jdbc/reference/setobject-method-sqlserverpreparedstatement.md)  
  
 Можно настроить способ отправки значения java.sql.Time с помощью **sendTimeAsDatetime** свойство соединения. Дополнительные сведения см. в разделе [задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
 Можно программно изменить значение **sendTimeAsDatetime** свойство соединения с [SQLServerDataSource.setSendTimeAsDatetime](../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md).  
  
 Версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] более раннюю, чем [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)] не поддерживают **время** тип данных, поэтому приложения, использующие java.sql.Time, обычно сохраняют java.sql.Time значения как **datetime** или **smalldatetime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] типов данных.  
  
 Если вы хотите использовать **datetime** и **smalldatetime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] типов данных при работе со значениями java.sql.Time, необходимо задать **sendTimeAsDatetime** Свойство соединения для **true**. Если вы хотите использовать **время** [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] типа данных при работе со значениями java.sql.Time, необходимо задать **sendTimeAsDatetime** свойства соединения **false**.  
  
 Имейте в виду, что если значения java.sql.Time в параметр, тип данных которого можно также хранение дат, то даты по умолчанию различаются в зависимости от того, является ли значения java.sql.Time отправляются в **datetime** (1/1/1970 г.) или **время** значение (1/1/1900 г.). Дополнительные сведения о преобразовании данных при отправке данных на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], в разделе [данных с использованием даты и времени](http://go.microsoft.com/fwlink/?LinkID=145211).  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] версии 3.0 драйвера JDBC **sendTimeAsDatetime** имеет значение true, если по умолчанию. В следующем выпуске **sendTimeAsDatetime** свойство соединения может быть задано значение false по умолчанию.  
  
 Чтобы убедиться, что приложение продолжает работать должным образом независимо от значения по умолчанию **sendTimeAsDatetime** свойства соединения, вы можете:  
  
-   Использовать java.sql.Time при работе с **время** [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] тип данных.  
  
-   Использовать java.sql.Timestamp при работе с **datetime**, **smalldatetime**, и **datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] типов данных.  
  
Обратите внимание, что sendTimeAsDatetime должен иметь значение false для зашифрованных столбцов, как зашифрованные столбцы не поддерживают преобразование из времени в дату-время. Класс SQLServerConnection, начиная с Microsoft JDBC Driver 6.0 для SQL Server, имеет следующие два метода set или get значение свойства sendTimeAsDatetime.

```
  public boolean getSendTimeAsDatetime()
  public void setSendTimeAsDatetime(boolean sendTimeAsDateTimeValue)
```
  
## <a name="see-also"></a>См. также  
 [Основные сведения о типах данных драйвера JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
