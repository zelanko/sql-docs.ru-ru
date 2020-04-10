---
title: Метод setString (SQLServerPreparedStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 25dabdc9-c60f-485a-87eb-306067964765
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d8f2c86379f445209442780aa2b07dbfa5073c12
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926565"
---
# <a name="setstring-method-sqlserverpreparedstatement"></a>Метод setString (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает назначенному параметру указанное значение **String**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setString(int index,  
                            java.lang.String str)  
```  
  
#### <a name="parameters"></a>Параметры  
 *index*  
  
 Значение **int**, определяющее номер параметра.  
  
 *str*  
  
 Значение типа **String**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setString определен с помощью метода setString в интерфейсе java.sql.PreparedStatement.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
