---
description: Метод getResponseBuffering (SQLServerStatement)
title: Метод getResponseBuffering (SQLServerStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getResponseBuffering()
apilocation:
- SQLServerStatement.getResponseBuffering()
apitype: Assembly
ms.assetid: a9a9ffdd-7ce3-4e0a-907c-34d6a54e6865
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 08411235fe8e571e9f3bdaf7220f2387d3a0b5c0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434796"
---
# <a name="getresponsebuffering-method-sqlserverstatement"></a>Метод getResponseBuffering (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает режим буферизации ответов для этого объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final java.lang.String getResponseBuffering()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Строка** со значением **full** или **adaptive** в нижнем регистре.  
  
## <a name="remarks"></a>Remarks  
 Режим **adaptive** указывает на буферизацию необходимого минимума данных.  
  
 Режим **full** указывает, что с сервера во время выполнения считывается весь результат.  
  
 Значение **adaptive** используется по умолчанию в версиях 2.0 и 3.0 драйвера JDBC. Значение **full** использовалось по умолчанию в драйвере JDBC до версии 2.0.  
  
 Дополнительные сведения об использовании режима буферизации ответов см. в статье [Использование адаптивной буферизации](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод setResponseBuffering (SQLServerStatement)](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)   
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
