---
title: Метод isSparseColumnSet (SQLServerResultSetMetaData) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ac363670-78ae-49f1-aeda-4fba3329a258
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 60862208a91f68260de9340b2ca9c4e51f115094
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
 **значение true,** Если столбца в результирующем наборе набор разреженных столбцов, в противном случае **false**.  
  
## <a name="remarks"></a>Замечания  
 Этот метод не извлекает данные из базы данных.  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [Элементы SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [Класс SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
