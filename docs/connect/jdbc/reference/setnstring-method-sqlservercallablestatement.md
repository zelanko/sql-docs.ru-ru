---
title: Метод setNString (SQLServerCallableStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6494300b-7fc0-4076-8311-22d35a96cdc6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: af608cdb956e24a59f508c1d9a661c64b9081a98
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80913620"
---
# <a name="setnstring-method-sqlservercallablestatement"></a>Метод setNString (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает назначенному параметру значение указанного объекта String.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setNString(java.lang.String parameterName, java.lang.String value)  
```  
  
#### <a name="parameters"></a>Параметры  
 *parameterName*  
  
 Значение **String**, которое указывает имя параметра.  
  
 *value*  
  
 Объект String.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод следует использовать для типов данных **NCHAR**, **NVARCHAR**, **NTEXT** и **XML**.  
  
 Этот метод setNString определен с помощью метода setNString в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
