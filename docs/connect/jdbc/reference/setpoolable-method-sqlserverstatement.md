---
title: Метод setPoolable (SQLServerStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f0f798c8-cafb-4acc-b85d-2e0059c91d92
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5424de7d0d6f7bda44ec61ea61f48d63bb097c97
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67973206"
---
# <a name="setpoolable-method-sqlserverstatement"></a>Метод setPoolable (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Запрашивает поддержку пулов или запрет пулов в инструкции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setPoolable(boolean poolable) throws SQLException  
```  
  
#### <a name="parameters"></a>Параметры  
 *поддерживает*  
  
 Если задано значение **true**, запрашивается поддержка пулов в инструкции. Если задано значение **false**, запрашивается запрет пулов в инструкции.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Значение, заданное в параметре *poolable*, служит подсказкой для реализации пула инструкций и указывает, требуется ли приложению поддержка пулов в инструкции. Диспетчер пула инструкций определяет, будет ли использоваться эта подсказка.  
  
 Значение пула инструкций применяется к внутренним кэшам инструкций, реализованным в драйвере, и внешним кэшам инструкций, реализованным на серверах приложений и в других приложениях.  
  
 По умолчанию объект SQLServerStatement не может быть в пуле при создании. Объекты SQLServerPreparedStatement и SQLServerCallableStatement могут быть объединены в пул при создании.  
  
 Если этот метод вызывается для закрытой инструкции, создается исключение [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md).  
  
 [isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md) возвращает значение, показывающее, поддерживает ли объект пулы.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
