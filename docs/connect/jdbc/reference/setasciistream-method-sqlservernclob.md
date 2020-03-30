---
title: Метод setAsciiStream (SQLServerNClob) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 617ece92-0fb1-4f95-b32d-29b5b56eb3fb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 043a94108bdb7c8938f06e8bf1d4bf58651fbf21
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67975374"
---
# <a name="setasciistream-method-sqlservernclob"></a>Метод setAsciiStream (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает поток, используемый для записи символов ASCII в значение **NCLOB**, представленное данным объектом **java.sql.NClob**, начиная с указанной позиции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.OutputStream setAsciiStream(long pos)  
```  
  
#### <a name="parameters"></a>Параметры  
 *pos*  
  
 Позиция, с которой начинается запись в объект **NCLOB**, начинается с 1.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект OutputStream, представляющий поток, в который можно записывать символы в кодировке ASCII.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setAsciiStream задается с помощью метода setAsciiStream в интерфейсе java.sql.NClob.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Элементы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Класс SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
