---
title: Метод getString (int) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getString (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f3fce8bf-8d6e-476f-aa6d-992daa79b899
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c8908a2ac8d6d591997d9a36c6d362c5a59c64e3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47652332"
---
# <a name="getstring-method-int"></a>Метод getString (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение заданного параметра в виде значения типа данных **String** на языке программирования Java по заданному индексу параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getString(int index)  
```  
  
#### <a name="parameters"></a>Параметры  
 *index*  
  
 Значение типа **int**, указывающее индекс параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **String**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getString определен с помощью метода getString в интерфейсе java.sql.CallableStatement.  
  
 Все столбцы в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] можно возвращать в виде строковых значений. Это значит, что можно возвращать строковое представление всех числовых и символьных типов, а также шестнадцатеричное представление двоичных столбцов, таких как binary, varbinary, varbinary(max), image, timestamp и uniqueidentifier.  
  
 Типы, зависящие от расположения, такие как money, smallmoney, datetime, smalldatetime, float, real, decimal и numeric, возвращают канонический формат toString() для базового значения типа.  
  
 Определяемые пользователем типы возвращаются в виде шестнадцатеричных строковых значений.  
  
## <a name="see-also"></a>См. также:  
 [Метод getString (SQLServerCallableStatement)](../../../connect/jdbc/reference/getstring-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
