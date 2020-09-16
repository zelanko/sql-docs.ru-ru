---
description: Метод prepareStatement (java.lang.String, java.lang.String)
title: Метод prepareStatement (java.lang.String, java.lang.String) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.prepareStatement
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e0db2871-3a5f-4fcc-af61-92333042dcd1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 51c8d9f09419c0d738bc819270c82a43471549be
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432896"
---
# <a name="preparestatement-method-javalangstring-javalangstring"></a>Метод prepareStatement (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Создает объект [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) для отправки в базу данных параметризованных инструкций SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.PreparedStatement prepareStatement(java.lang.String sql,  
                                                   java.lang.String[] columnNames)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sql*  
  
 Значение **String**, содержащее инструкцию SQL.  
  
 *columnNames*  
  
 Массив **String** имен столбцов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект PreparedStatement.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод prepareStatement определяется методом prepareStatement в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также:  
 [Метод prepareStatement (SQLServerConnection)](../../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md)   
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
