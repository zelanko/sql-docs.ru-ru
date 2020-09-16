---
description: Метод setResponseBuffering (SQLServerStatement)
title: Метод setResponseBuffering (SQLServerStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apilocation:
- SQLServerStatement.setResponseBuffering(String responseBufferingValue)
apitype: Assembly
ms.assetid: 9f489835-6cda-4c8c-b139-079639a169cf
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d4432c50432a22e7c0700c464a0d1f6d37f32cfa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458436"
---
# <a name="setresponsebuffering-method-sqlserverstatement"></a>Метод setResponseBuffering (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает режиму буферизации ответов для этого объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) значение **String full** или **adaptive** без учета регистра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setResponseBuffering(java.lang.String value)  
```  
  
#### <a name="parameters"></a>Параметры  
 *value*  
  
 **Строка**, содержащая режим буферизации ответов. Допустимый режим может быть одной из следующих строк без учета регистра: **full** или **adaptive**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Режим **adaptive** указывает на буферизацию необходимого минимума данных.  
  
 Режим **full** указывает, что с сервера во время выполнения считывается весь результат.  
  
 Значение adaptive используется по умолчанию в версиях 2.0 и 3.0 драйвера JDBC. Значение full использовалось по умолчанию в драйвере JDBC до версии 2.0.  
  
 Метод [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) позволяет отменить соединение **responseBuffering** свойства **String** для текущего объекта [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md). Дополнительные сведения об использовании режима буферизации ответов см. в статье [Использование адаптивной буферизации](../../../connect/jdbc/using-adaptive-buffering.md).  
  
 Если приложение указывает недопустимое значение параметра для метода [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md), возникает исключение [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)   
 [Использование адаптивной буферизации](../../../connect/jdbc/using-adaptive-buffering.md)  
  
  
