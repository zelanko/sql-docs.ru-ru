---
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
ms.openlocfilehash: 7ded6641232939ce0f76ade9f332646bbdd4c4d3
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927828"
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
  
  
