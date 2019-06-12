---
title: Метод getNString (int) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2048bb9f-7d9b-4aaa-b135-c716910cc800
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 03a11c4479ac860e84009fcd528d932098bdc661
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66784352"
---
# <a name="getnstring-method-int"></a>Метод getNString (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение заданного **NCHAR**, **NVARCHAR**, или **LONGNVARCHAR** параметра в виде строки на Java языка программирования.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final java.lang.String getNString(int parameterIndex)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterIndex*  
  
 Значение типа **int**, указывающее индекс параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 AStringobject.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getString определен с помощью метода getString в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод getNString (SQLServerCallableStatement)](../../../connect/jdbc/reference/getnstring-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
