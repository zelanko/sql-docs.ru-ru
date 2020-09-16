---
description: Метод setSavepoint (java.lang.String)
title: Метод setSavepoint (java.lang.String) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setSavepoint (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1cf15ec4-d9d9-4ab3-bfee-2ea43ff609a6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 57ed08c322b8579b92165306397fb26312d95fa3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458428"
---
# <a name="setsavepoint-method-javalangstring"></a>Метод setSavepoint (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Создает в текущей транзакции точку сохранения с указанным именем и возвращает новый объект [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md), который ее представляет.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Savepoint setSavepoint(java.lang.String sName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sName*  
  
 Значение **String**, содержащее имя точки сохранения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект SavePoint.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setSavePoint определяется методом setSavePoint в интерфейсе java.sql.Connection.  
  
 Аргумент *sName* автоматически экранируется драйвером [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Метод setSavepoint (SQLServerConnection)](../../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)   
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
