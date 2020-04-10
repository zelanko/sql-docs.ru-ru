---
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
ms.openlocfilehash: f3a6765bf5665704293233293982edfc1e746ce5
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927447"
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
  
  
