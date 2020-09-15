---
description: Метод updateRef (int, java.sql.Ref)
title: Метод updateRef (int, java.sql.Ref) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateRef (int, java.sql.Ref)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: eab3ebae-3f68-4303-869a-fee06e3a9c71
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9358fdc1c788e2e2be19b4999c3d10ca825d2799
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88353170"
---
# <a name="updateref-method-int-javasqlref"></a>Метод updateRef (int, java.sql.Ref)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец значением java.sql.Ref по заданному индексу столбца.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateRef(int columnIndex,  
                      java.sql.Ref x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 Значение типа **int**, указывающее индекс столбца.  
  
 *x*  
  
 Объект Ref.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод updateRef определен с помощью метода updateRef в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateRef (SQLServerResultSet)](../../../connect/jdbc/reference/updateref-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
