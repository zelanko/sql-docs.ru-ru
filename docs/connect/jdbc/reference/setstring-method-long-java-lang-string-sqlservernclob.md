---
description: Метод setString (long, java.lang.String) (SQLServerNClob)
title: Метод setString (long, java.lang.String) в NClob | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 698073b2-3f0c-449c-ad68-48144698fe8f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 944277e0bf3b8a701ceb9700f4b70a71cdec8d25
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450754"
---
# <a name="setstring-method-long-javalangstring-sqlservernclob"></a>Метод setString (long, java.lang.String) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Записывает заданную **строку** в **NCLOB**, начиная с указанной позиции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int setString(long pos,  
              java.lang.String str)  
```  
  
#### <a name="parameters"></a>Параметры  
 *pos*  
  
 Позиция, с которой начнется запись в **NCLOB**, начинается с 1.  
  
 *str*  
  
 Строка для записи в **NCLOB**.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Количество записанных символов.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setString определен с помощью метода setString в интерфейсе java.sql.NClob.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Элементы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Класс SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
