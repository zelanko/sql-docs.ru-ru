---
title: Метод moveToCurrentRow (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.moveToCurrentRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9a7c754c-2d72-4207-b3bd-2afc6047fb3d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8957ed221a3d06669100d139b87af0427d0b00af
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80914830"
---
# <a name="movetocurrentrow-method-sqlserverresultset"></a>Метод moveToCurrentRow (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Перемещает курсор в сохраненное местоположение курсора, то есть обычно в текущую строку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void moveToCurrentRow()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод moveToCurrentRow задается с помощью метода moveToCurrentRow в интерфейсе java.sql.ResultSet.  
  
 Этот метод не выполняет никаких действий, если курсор не находится в строке вставки.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
