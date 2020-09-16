---
description: Метод position (java.sql.NClob, long)
title: Метод position (java.sql.NClob, long) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f2354278-d128-4cf4-a170-22c05fcb763b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e810a05d5c289babe665a398f27a670349c2b304
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433016"
---
# <a name="position-method-javasqlnclob-long"></a>Метод position (java.sql.NClob, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает символьную позицию, с которой начинается значение свойства *searchstr* указанного объекта **NClob** в этом же объекте **NClob**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
long position(java.sql.NClob searchstr,  
              long start)  
```  
  
#### <a name="parameters"></a>Параметры  
 *searchstr*  
  
 Искомый объект NClob.  
  
 *start*  
  
 Позиция, с которой начнется поиск; отсчитывается от 1.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Позиция, в которой находится подстрока, либо значение -1, если она не найдена. Позиция отсчитывается от 1.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод position задается с помощью метода position в интерфейсе java.sql.NClob.  
  
## <a name="see-also"></a>См. также:  
 [Метод position (SQLServerNClob)](../../../connect/jdbc/reference/position-method-sqlservernclob.md)   
 [Методы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Элементы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Класс SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
