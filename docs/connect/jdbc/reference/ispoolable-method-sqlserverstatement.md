---
title: Метод isPoolable (SQLServerStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b8a12ac5-57cb-4288-9973-c7d5cebd197c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 225584f3c60f0494af987581574d8f4205e04e2d
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67977514"
---
# <a name="ispoolable-method-sqlserverstatement"></a>Метод isPoolable (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, показывающее, можно ли добавить инструкцию в предоставляемый пользователем пул инструкций.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean isPoolable() throws SQLException  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если инструкцию можно добавить в предоставляемый пользователем пул инструкций. В противном случае значение — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 [setPoolable](../../../connect/jdbc/reference/setpoolable-method-sqlserverstatement.md) изменяет объединенное поведение объекта.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
