---
title: Метод setInt (SQLServerCallableStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setInt
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7de05cf4-3a48-4c60-9a1b-6ad2ae43d258
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a2a4afa586e060b5e05d1f3d9f5ace8f0ce41d9d
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922258"
---
# <a name="setint-method-sqlservercallablestatement"></a>Метод setInt (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает для указанного параметра указанное значение **int**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setInt(java.lang.String sCol,  
                   int i)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sCol*  
  
 Значение типа **String**, содержащее имя параметра.  
  
 *i*  
  
 Значение **int**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setInt определен с помощью метода setInt в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
