---
title: Метод setString (long, java.lang.String, int, int) в NClob | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2d5e9f50-15b2-4c76-8bfc-3b5be49c2781
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 074983f08e837f3a895ddc8884e5ac140033c51e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67972740"
---
# <a name="setstring-method-long-javalangstring-int-int-sqlservernclob"></a>Метод setString (long, java.lang.String, int, int) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Записывает указанную строку в NCLOB, начиная с заданного положения на основе указанного смещения и длины.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int setString(long pos,  
              java.lang.String str,  
              int offset,  
              int len)  
```  
  
#### <a name="parameters"></a>Параметры  
 *POS*  
  
 Позиция, с которой начнется запись в **NCLOB**, начинается с 1.  
  
 *str*  
  
 Строка для записи в **NCLOB**.  
  
 *offset*  
  
 Смещение в *str* для начала чтения записываемых символов.  
  
 *len*  
  
 Количество записываемых символов.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setString определен с помощью метода setString в интерфейсе java.sql.NClob.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Элементы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Класс SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
