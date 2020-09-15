---
description: Метод setFetchDirection (SQLServerStatement)
title: Метод setFetchDirection (SQLServerStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 18176517-2fb3-4266-924d-0f01253083d2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7e9469fe9b0e559358e3e18c15719161b0ae0033
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431876"
---
# <a name="setfetchdirection-method-sqlserverstatement"></a>Метод setFetchDirection (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Дает [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] указание относительно направления, в котором будут обрабатываться строки результирующего набора.  
  
> [!NOTE]  
>  Драйвер JDBC в настоящее время пропускает указание, определенное этим методом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setFetchDirection(int nDir)  
```  
  
#### <a name="parameters"></a>Параметры  
 *nDir*  
  
 Значение типа **int**, указывающее направление обработки строк, может принимать одно из следующих значений:  
  
 FETCH_FORWARD  
  
 FETCH_REVERSE  
  
 FETCH_UNKNOWN  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setFetchDirection задается с помощью метода setFetchDirection в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
