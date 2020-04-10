---
title: Метод getInt (int) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getInt (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c86792bb-096e-4c58-8b9e-74491ccf83a6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 484830d5bdf8ed00334a7f695f4f67f31e13f565
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921499"
---
# <a name="getint-method-int"></a>Метод getInt (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение заданного параметра в виде значения типа **int** на языке программирования Java по заданному индексу параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getInt(int index)  
```  
  
#### <a name="parameters"></a>Параметры  
 *index*  
  
 Значение типа **int**, указывающее индекс параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getInt указывается методом getInt в интерфейсе java.sql.CallableStatement.  
  
 Этот метод поддерживается только для типов данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], таких как int, smallint, tinyint и bit, которые могут безопасно возвращать целочисленное значение. Использование этого метода при работе со столбцами других типов данных приведет к возникновению исключения.  
  
## <a name="see-also"></a>См. также:  
 [Метод getInt (SQLServerCallableStatement)](../../../connect/jdbc/reference/getint-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
