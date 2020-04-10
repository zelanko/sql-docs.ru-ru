---
title: Метод setFetchDirection (SQLServerResultSet) | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6f0055facd8248816da07fea74e8dc8035f78d84
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922355"
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
 Этот метод setFetchDirection задается с помощью метода setFetchDirection в интерфейсе java.sql.ResultSet.  
  
 Исходное значение этого метода определяется объектом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), создавшим этот объект SQLServerResultSet. Направление выборки может быть изменено в любой момент.  
  
> [!NOTE]  
>  Если курсор однопроходной, то при использовании этого метода направление изменено не будет.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
