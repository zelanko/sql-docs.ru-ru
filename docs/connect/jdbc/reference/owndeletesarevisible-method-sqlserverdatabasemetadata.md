---
title: Метод ownDeletesAreVisible (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.ownDeletesAreVisible
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2dd6d976-9f8f-4a24-9354-ff239cfd4364
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ecb8ca48f9f4b76a9d3bf22aff3930eec63667dc
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67976549"
---
# <a name="owndeletesarevisible-method-sqlserverdatabasemetadata"></a>Метод ownDeletesAreVisible (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, являются ли видимыми собственные операции удаления результирующего набора.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean ownDeletesAreVisible(int type)  
```  
  
#### <a name="parameters"></a>Параметры  
 *type*  
  
 Значение типа **int**, указывающее тип результирующего набора. Оно может быть равно следующим значениям, определенным в java.sql.ResultSet или SQLServerResultSet:  
  
## <a name="javasqlresultset-types"></a>Типы java.sql.ResultSet  
 TYPE_FORWARD_ONLY  
  
 TYPE_SCROLL_SENSITIVE  
  
 TYPE_SCROLL_INSENSITIVE  
  
## <a name="sqlserverresultset-types"></a>Типы SQLServerResultSet  
 TYPE_SS_SCROLL_STATIC  
  
 TYPE_SS_SCROLL_KEYSET  
  
 TYPE_SS_DIRECT_FORWARD_ONLY  
  
 TYPE_SS_SERVER_CURSOR_FORWARD_ONLY  
  
 TYPE_SS_SCROLL_DYNAMIC  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если операции удаления видимы. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод ownDeletesAreVisible задается с помощью метода ownDeletesAreVisible в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
