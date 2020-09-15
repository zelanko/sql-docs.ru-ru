---
description: Метод setEscapeProcessing (SQLServerStatement)
title: Метод setEscapeProcessing (SQLServerStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setEscapeProcessing
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6ac0682e-e04c-4fdb-893b-92408d42051e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b8864c591a72fdeabc5dd61ee7df34dcdc5f61c1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431906"
---
# <a name="setescapeprocessing-method-sqlserverstatement"></a>Метод setEscapeProcessing (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задается режим обработки escape-последовательностей.  
  
> [!NOTE]  
>  Для [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] обработка escape-последовательностей всегда включена. Если установить значение false в этом методе, обработка останется включенной.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setEscapeProcessing(boolean enable)  
```  
  
#### <a name="parameters"></a>Параметры  
 *enable*  
  
 Значение **true**, чтобы включить обработку escape-последовательностей. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setEscapeProcessing задается с помощью метода setEscapeProcessing в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
