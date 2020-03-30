---
title: Метод isStatementPoolingEnabled (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.isStatementPoolingEnabled
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d2f5178c8a2ce5b527ce70e6a3d8fc139ccc9c72
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67977198"
---
# <a name="isstatementpoolingenabled-method-sqlserverconnection"></a>Метод isStatementPoolingEnabled (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Возвращает сведения о том, включено ли создание пула инструкций для этого подключения.

## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean isStatementPoolingEnabled()  
```  

## <a name="return-value"></a>Возвращаемое значение
 **Логическое значение**, содержащее флаг, который указывает на то, включено ли создание пула инструкций.

## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 Этот метод доступен в драйвере JDBC 6.4 и более поздних версий.
 
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
