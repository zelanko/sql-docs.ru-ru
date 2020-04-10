---
title: Метод getShort (java.lang.String) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getShort (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cd39ed03-b3e8-443d-9c7a-e8cf2581e581
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c7ab0b9ece4fb9f251d7d07033c1867c242235f0
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924147"
---
# <a name="getshort-method-javalangstring"></a>Метод getShort (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение заданного параметра в виде значения типа **short** на языке программирования Java по указанному имени параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public short getShort(java.lang.String sCol)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sCol*  
  
 Значение типа **String**, содержащее имя параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **short**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getShort определен с помощью метода getShort в интерфейсе java.sql.CallableStatement.  
  
 Этот метод поддерживается только для типов данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], таких как smallint, tinyint и bit, которые могут безопасно возвращать целочисленное значение. Использование этого метода при работе со столбцами других типов данных приведет к возникновению исключения.  
  
## <a name="see-also"></a>См. также:  
 [Метод getShort (SQLServerCallableStatement)](../../../connect/jdbc/reference/getshort-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
