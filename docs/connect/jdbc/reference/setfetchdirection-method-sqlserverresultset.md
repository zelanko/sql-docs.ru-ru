---
title: Метод setFetchDirection (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.setFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4ee82290-508d-4bff-a5c5-8a56338deef8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d801a0184259ae22f86ea5ec23391ef78b23ce38
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67974264"
---
# <a name="setfetchdirection-method-sqlserverresultset"></a>Метод setFetchDirection (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Дает указание относительно направления, в котором будут обрабатываться строки в этом объекте [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
> [!NOTE]  
>  Сейчас этот метод не поддерживается [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. При использовании этого метода драйвер JDBC запоминает настройки, но не использует их в текущий момент.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setFetchDirection(int direction)  
```  
  
#### <a name="parameters"></a>Параметры  
 *direction*  
  
 Значение **int**, которое указывает предполагаемое направление выборки. Может использоваться одно из следующих значений:  
  
 ResultSet.FETCH_FORWARD  
  
 ResultSet.FETCH_REVERSE  
  
 ResultSet.FETCH_UNKNOWN  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setFetchDirection задается методом setFetchDirection в интерфейсе Java. SQL. Result.  
  
 Исходное значение этого метода определяется объектом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), создавшим этот объект SQLServerResultSet. Направление выборки может быть изменено в любой момент.  
  
> [!NOTE]  
>  Если курсор однопроходной, то при использовании этого метода направление изменено не будет.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
