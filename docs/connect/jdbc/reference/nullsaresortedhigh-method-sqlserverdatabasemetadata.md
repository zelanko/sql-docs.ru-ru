---
title: Метод nullsAreSortedHigh (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.nullsAreSortedHigh
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6ff97d37-befc-47b1-8092-505917216a41
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3e60c5a3388a58e49e824f7ec768edb227c7375d
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923078"
---
# <a name="nullsaresortedhigh-method-sqlserverdatabasemetadata"></a>Метод nullsAreSortedHigh (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, считаются ли значения NULL большими при сортировке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean nullsAreSortedHigh()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если значения сортируются по увеличению. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод nullsAreSortedHigh задается с помощью метода nullsAreSortedHigh в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
