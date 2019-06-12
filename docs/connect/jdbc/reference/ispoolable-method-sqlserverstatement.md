---
title: Метод isPoolable (SQLServerStatement) | Документация Майкрософт
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
manager: jroth
ms.openlocfilehash: a5fcc6d842299884bec758ca66f303bf3e8ed625
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796469"
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
  
  
