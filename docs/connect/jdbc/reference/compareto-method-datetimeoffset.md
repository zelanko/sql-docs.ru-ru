---
title: Метод compareTo (DateTimeOffset) | Документация Майкрософт
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
ms.openlocfilehash: 3f70413a7624b9bbd380a664fbf61b9a33f8989b
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67955516"
---
# <a name="compareto-method-datetimeoffset"></a>Метод compareTo (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Сравнивает данный объект **DateTimeOffset** с другим объектом **DateTimeOffset** по критерию совпадения времени GMT.  
  
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
|0|Оба объекта **DateTimeOffset** представляют одну и ту же точку во времени.|  
|Отрицательное число|Данный объект **DateTimeOffset** представляет точку во времени, предшествующую *другому объекту*.|  
|Положительное число|Данный объект **DateTimeOffset** представляет точку во времени позднее *другого объекта*.|  
  
## <a name="remarks"></a>Remarks  
 Если два объекта **DateTimeOffset** имеют одно и то же время GMT, то дополнительное упорядочение объектов по смещению не производится.  
  
## <a name="see-also"></a>См. также:  
 [Класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Элементы DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
