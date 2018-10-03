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
manager: craigg
ms.openlocfilehash: b5f135ac405a5dbeda6a0c86d447e591c8bee9a1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47755342"
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
  
  
