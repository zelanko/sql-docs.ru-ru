---
title: Метод insertsAreDetected (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.insertsAreDetected
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f296cc42-9d26-48c3-a360-bcf51c31f7fb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ba9fb6ef4a1a7166709620cad1bbaa36cd0ed257
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80910020"
---
# <a name="insertsaredetected-method-sqlserverdatabasemetadata"></a>Метод insertsAreDetected (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, обнаруживается ли вставка видимой строки вызовом метода [rowInserted](../../../connect/jdbc/reference/rowinserted-method-sqlserverresultset.md) класса [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean insertsAreDetected(int type)  
```  
  
#### <a name="parameters"></a>Параметры  
 *type*  
  
 Целочисленное значение, указывающее тип результирующего набора. Возможно одно из следующих значений, определенных в java.sql.ResultSet или SQLServerResultSet.  
  
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
 Значение **true**, если можно обнаружить вставку строки. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод insertsAreDetected задается с помощью метода insertsAreDetected в интерфейсе java.sql.DatabaseMetaData.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не обнаруживает вставленные строки ни для одного типа курсора.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
