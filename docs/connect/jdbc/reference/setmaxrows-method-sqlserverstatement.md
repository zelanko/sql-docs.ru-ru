---
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
ms.openlocfilehash: 0dbecd7bd953c43980b307e6737ea1390511fa1a
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925779"
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
  
  
