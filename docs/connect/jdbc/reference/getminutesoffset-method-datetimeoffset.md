---
title: Метод getMinutesOffset (DateTimeOffset) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 18ba844a-ea36-42de-87da-bbc222082efe
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6d17b5451340c07ea8c9bd0ce61bf858b419b121
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66784762"
---
# <a name="getminutesoffset-method-datetimeoffset"></a>Метод getMinutesOffset (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает смещение в минутах относительно GMT, этот объект DateTimeOffset.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getMinutesOffset()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Смещение в минутах.  
  
## <a name="remarks"></a>Remarks  
 Для DateTimeOffset объекта, представляющего 8 марта 2010 г. 11:35:48 -0800, getMinutesOffset возвращает значение 480.  
  
## <a name="see-also"></a>См. также:  
 [Класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Элементы DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
