---
title: Метод setCharacterStream (java.lang.String, java.io.Reader) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 43acac5b-5a8a-4685-bee6-7194d2d03a52
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3d7bf3883ad7cab14ac2313eda5b00710bfcdbc3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67974671"
---
# <a name="setcharacterstream-method-javalangstring-javaioreader"></a>Метод setCharacterStream (java.lang.String, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает указанному параметру заданный объект Reader.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setCharacterStream(java.lang.String parameterName,  
                                             java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterName*  
  
 Значение типа **String**, содержащее имя параметра.  
  
 *reader*  
  
 Объект Reader, содержащий данные в Юникоде.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setCharacterStream задается с помощью метода setCharacterStream в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод setCharacterStream (SQLServerCallableStatement)](../../../connect/jdbc/reference/setcharacterstream-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  
