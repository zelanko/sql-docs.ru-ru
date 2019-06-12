---
title: Метод compareTo (DateTimeOffset) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e4cf2ea4-0fe9-40ce-ba79-f2a2b616997e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: cb06138639be09378baa8dfe94d110c0ded41223
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66777372"
---
# <a name="compareto-method-datetimeoffset"></a>Метод compareTo (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Сравнивает этот **DateTimeOffset** объект с другим объектом **DateTimeOffset** объекта на основе времени по Гринвичу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int compareTo(DateTimeOffset other)  
```  
  
#### <a name="parameters"></a>Параметры  
 Значение [DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md), которое нужно сравнить с текущим экземпляром.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В следующей таблице описывается значение, возвращаемое данным методом.  
  
|Возвращаемое значение|Описание|  
|------------------|-----------------|  
|0|Оба **DateTimeOffset** объекты представляют тот же момент времени.|  
|Отрицательное число|Это **DateTimeOffset** объект представляет точку во времени, предшествующий *других*.|  
|Положительное число|Это **DateTimeOffset** объект представляет точку во времени, которое находится за *других*.|  
  
## <a name="remarks"></a>Remarks  
 Если два объекта **DateTimeOffset** имеют одно и то же время GMT, то дополнительное упорядочение объектов по смещению не производится.  
  
## <a name="see-also"></a>См. также:  
 [Класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Элементы DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
