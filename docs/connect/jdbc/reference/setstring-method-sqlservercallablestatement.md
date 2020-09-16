---
description: Метод setString (SQLServerCallableStatement)
title: Метод setString (SQLServerCallableStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f38b97b5-d4f0-4f74-a33d-740241a85842
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6ab66f76ccc0f6c80c9358e56902c063ca5e1e15
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450718"
---
# <a name="setstring-method-sqlservercallablestatement"></a>Метод setString (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает назначенному параметру указанное значение **String** Java.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setString(java.lang.String sCol,  
                      java.lang.String s)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sCol*  
  
 Значение типа **String**, содержащее имя параметра.  
  
 *s*  
  
 Значение типа **String**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setString указывается методом setString в интерфейсе java.sql.CallableStatement.  
  
 Преобразования строкового типа данных в двоичный тип выполняются только в том случае, когда драйверу [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] известно, что целевой объект имеет двоичный тип. В случаях, когда драйверу JDBC неизвестен базовый тип, он будет передавать литерал **String** и возвращать ошибку сервера, если сервер не может выполнить преобразование.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
