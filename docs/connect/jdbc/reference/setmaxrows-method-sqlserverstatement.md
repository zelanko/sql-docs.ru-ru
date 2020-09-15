---
description: Метод setMaxRows (SQLServerStatement)
title: Метод setMaxRows (SQLServerStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setMaxRows
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cccc0667-589b-4655-8ea8-14ae8b2eb9dc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 544eb34b40bc81afbed34809f3348c5649c3d0be
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431766"
---
# <a name="setmaxrows-method-sqlserverstatement"></a>Метод setMaxRows (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает равное заданному числу ограничение для максимального количества строк, которое может содержаться в объекте [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setMaxRows(int max)  
```  
  
#### <a name="parameters"></a>Параметры  
 *max*  
  
 Значение типа **int**, указывающее максимальное число строк. Если ограничения нет, то значение равно 0.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setMaxRows задается с помощью метода setMaxRows в интерфейсе java.sql.Statement.  
  
 Этот метод setMaxRows не влияет на динамические прокручиваемые курсоры. В этом приложении следует с помощью синтаксиса SELECT TOP N SQL ограничивать число строк, возвращаемых из потенциально больших результирующих наборов.  
  
 При вызове метода setMaxRows [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] при обработке запроса приложения выполняет инструкцию SQL SET ROWCOUNT. При этом JDBC Driver ограничивает максимальное число строк для всех инструкций [!INCLUDE[tsql](../../../includes/tsql-md.md)], выполняемых этим запросом, а не только число возвращаемых строк. Если в приложении нужно задать предел только для объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) высшего уровня, то в запросе необходимо использовать синтаксис SQL SELECT TOP N вместо метода setMaxRows.  
  
 Дополнительные сведения об инструкции SQL SET ROWCOUNT см. в разделе "[SET ROWCOUNT (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=139522)" электронной документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
