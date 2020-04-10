---
title: Метод setFetchSize (SQLServerStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setFetchSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 760e555e-9667-4b40-b0ba-778026ff2923
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9fa7be5cc2f0e3f39e3d89881d38fb91a525b545
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922320"
---
# <a name="setfetchsize-method-sqlserverstatement"></a>Метод setFetchSize (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Определяет для драйвера [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] указание относительно числа строк, которые должны быть получены из базы данных, когда необходимы дополнительные строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setFetchSize(int rows)  
```  
  
#### <a name="parameters"></a>Параметры  
 *rows*  
  
 Значение **int**, которое указывает число извлекаемых строк.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setFetchSize задается с помощью метода setFetchSize в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
