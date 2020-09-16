---
description: Метод isSparseColumnSet (SQLServerResultSetMetaData)
title: Метод isSparseColumnSet (SQLServerResultSetMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ac363670-78ae-49f1-aeda-4fba3329a258
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 86fbbcdc34259e6b3d783d34ca77af57bcfba89f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433376"
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
  
  
