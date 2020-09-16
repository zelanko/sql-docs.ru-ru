---
description: Метод setSendTimeAsDatetime (SQLServerDataSource)
title: Метод setSendTimeAsDatetime (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 705a0494-b5e2-43db-940a-1b8cec550cdb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 52136134199ac4811d22b48bfbad768dbcdf8e7d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458419"
---
# <a name="setsendtimeasdatetime-method-sqlserverdatasource"></a>Метод setSendTimeAsDatetime (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Этот метод добавлен в версии 3.0 драйвера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC.  
  
 Изменяет значение свойства подключения **sendTimeAsDatetime**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setSendTimeAsDatetime(boolean sendTimeAsDateTime)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sendTimeAsDateTime*  
  
 Значение типа Boolean. Если задано значение true, то значения java.sql.Time отправляются на сервер как типы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **datetime**. Если задано значение false, то значения java.sql.Time отправляются на сервер как типы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **time**.  
  
## <a name="remarks"></a>Remarks  
 [SQLServerDataSource.getSendTimeAsDatetime](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md) возвращает значение свойства соединения **sendTimeAsDatetime**.  
  
 Дополнительные сведения о свойстве подключения **sendTimeAsDatetime** см. в статье о [настройке свойств подключения](../../../connect/jdbc/setting-the-connection-properties.md).  
  
 Дополнительные сведения см. в статье [Настройка способа отправки значений java.sql.Time на сервер](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
