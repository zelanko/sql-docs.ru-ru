---
title: Метод position (java.lang.String, long) (SQLServerNClob) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 46d4beec-831a-449f-98b6-322a80cc499a
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: faf6af6e1d52102b6f6358f2adc8a125ac1ef18a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802456"
---
# <a name="position-method-javalangstring-long-sqlservernclob"></a>Метод position (java.lang.String, long) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает позицию символа, по которому указанной подстроки *searchstr* отображается в **NCLOB** значению, представленному данным объектом **NClob** объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public long position(java.lang.String searchstr,  
              long start)  
```  
  
#### <a name="parameters"></a>Параметры  
 *searchstr*  
  
 Подстрока для поиска.  
  
 *start*  
  
 Позиция, с которой начнется поиск; отсчитывается от 1.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Позиция, в которой находится подстрока, либо значение -1, если она не найдена. Позиция отсчитывается от 1.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод позиция указывается с помощью метода положение в интерфейсе java.sql.NClob.  
  
## <a name="see-also"></a>См. также:  
 [Метод Position &#40;SQLServerNClob&#41;](../../../connect/jdbc/reference/position-method-sqlservernclob.md)   
 [Методы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Элементы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Класс SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
