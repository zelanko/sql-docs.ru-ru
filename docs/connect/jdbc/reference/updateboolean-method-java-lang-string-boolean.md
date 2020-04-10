---
title: Метод updateBoolean (java.lang.String, boolean) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateBoolean (java.lang.String, boolean)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5fed9ebb-d9a3-4d1a-9212-1057a603c4e5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1319bb034c4ce7d88a7145d97a2b6d71d3b92bc3
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928087"
---
# <a name="updateboolean-method-javalangstring-boolean"></a>Метод updateBoolean (java.lang.String, boolean)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец значением **boolean** по заданному имени столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateBoolean(java.lang.String columnName,  
                          boolean x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Значение типа **String**, содержащее имя столбца.  
  
 *x*  
  
 Значение **boolean**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateBoolean задается с помощью метода updateBoolean в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateBoolean (SQLServerResultSet)](../../../connect/jdbc/reference/updateboolean-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
