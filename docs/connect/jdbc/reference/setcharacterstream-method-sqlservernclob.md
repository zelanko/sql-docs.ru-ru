---
title: Метод setCharacterStream (SQLServerNClob) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 09042ee9-dfb1-4d0b-82bd-d1224b0aea80
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dc966b97231f491a5f3c2cdb71c457f0324a8df3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67974849"
---
# <a name="setcharacterstream-method-sqlservernclob"></a>Метод setCharacterStream (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает поток, используемый для записи символов Юникода в значение **NCLOB**, представленное этим объектом **java.sql.NClob**, начиная с указанной позиции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.Writer setCharacterStream(long pos)  
```  
  
#### <a name="parameters"></a>Параметры  
 *POS*  
  
 Позиция, с которой начнется запись в значение **NCLOB**, начинается с 1.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект записи представляет поток, в который могут записываться символы в Юникоде.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setCharacterStream задается методом setCharacterStream в интерфейсе Java. SQL. NClob.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Элементы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Класс SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
