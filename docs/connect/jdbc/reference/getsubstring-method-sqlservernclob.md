---
title: Метод getSubString (SQLServerNClob) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1d91c930-1bac-4da9-b9a5-ac2cfd31541b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1f84e1ab88eee80a4d73cc04f301a7c588950c25
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926166"
---
# <a name="getsubstring-method-sqlservernclob"></a>Метод getSubString (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает копию указанной подстроки в **NCLOB** по указанной начальной позиции и числу символов для копирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getSubString(long pos,  
                                  int length)  
```  
  
#### <a name="parameters"></a>Параметры  
 *pos*  
  
 Первый символ извлекаемой подстроки. Первый символ находится в позиции 1.  
  
 *length*  
  
 Количество копируемых последовательных символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **String**, указывающее подстроку в объекте **CLOB**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getSubString определен с помощью метода getSubString в интерфейсе java.sql.NClob.  
  
 При попытке получения нулевых символов из NCLOB со значением NULK или с нулевой длиной возвращается пустая строка. При попытке получить длину символов, начиная с позиции, отличной от 1 (первой), для NCLOB нулевой длины возникнет исключение по позиции.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Элементы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Класс SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
