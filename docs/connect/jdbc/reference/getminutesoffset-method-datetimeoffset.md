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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 350a1f63eefa87eccbca7ba0a12c4381ab820854
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80906166"
---
# <a name="getminutesoffset-method-datetimeoffset"></a>Метод getMinutesOffset (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает смещение в минутах относительно времени GMT для данного объекта DateTimeOffset.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getMinutesOffset()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Смещение в минутах.  
  
## <a name="remarks"></a>Remarks  
 Для объекта DateTimeOffset, представляющего 8 марта 2010 г., 11:35:48 -0800, метод getMinutesOffset возвращает значение 480.  
  
## <a name="see-also"></a>См. также:  
 [Класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Элементы DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  
