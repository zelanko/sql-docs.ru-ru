---
title: Метод isSparseColumnSet (SQLServerResultSetMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ac363670-78ae-49f1-aeda-4fba3329a258
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6d40bcf6f43f0323131ece954889459018340379
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796333"
---
# <a name="issparsecolumnset-method-sqlserverresultsetmetadata"></a>Метод isSparseColumnSet (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает, является ли столбец из результирующего набора набором разреженных столбцов.  
  
## <a name="syntax"></a>Синтаксис  
  
```scr  
public boolean isSparseColumnSet(int column)  
```  
  
#### <a name="parameters"></a>Параметры  
 *column*  
  
 Индекс столбца (начинающийся с единицы).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если столбец из результирующего набора является набором разреженных столбцов. В противном случае ― **false**.  
  
## <a name="remarks"></a>Remarks  
 Этот метод не извлекает данные из базы данных.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [Элементы SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [Класс SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
