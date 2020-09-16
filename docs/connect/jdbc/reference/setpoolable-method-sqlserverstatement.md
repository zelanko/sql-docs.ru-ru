---
description: Метод setPoolable (SQLServerStatement)
title: Метод setPoolable (SQLServerStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f0f798c8-cafb-4acc-b85d-2e0059c91d92
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f75e1ffad80d1442689da6d32eafcaf74cb48fdf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458476"
---
# <a name="setpoolable-method-sqlserverstatement"></a>Метод setPoolable (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Запрашивает поддержку пулов или запрет пулов в инструкции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setPoolable(boolean poolable) throws SQLException  
```  
  
#### <a name="parameters"></a>Параметры  
 *poolable*  
  
 Если задано значение **true**, запрашивается поддержка пулов в инструкции. Если задано значение **false**, запрашивается запрет пулов в инструкции.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Значение, заданное в параметре *poolable*, служит подсказкой для реализации пула инструкций и указывает, требуется ли приложению поддержка пулов в инструкции. Диспетчер пула инструкций определяет, будет ли использоваться эта подсказка.  
  
 Значение пула инструкций применяется к внутренним кэшам инструкций, реализованным в драйвере, и внешним кэшам инструкций, реализованным на серверах приложений и в других приложениях.  
  
 По умолчанию создаваемый объект SQLServerStatement не поддерживает включение в пул. Создаваемые объекты SQLServerPreparedStatement и SQLServerCallableStatement поддерживают включение в пул.  
  
 Если этот метод вызывается для закрытой инструкции, создается исключение [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md).  
  
 [isPoolable](../../../connect/jdbc/reference/ispoolable-method-sqlserverstatement.md) возвращает значение, показывающее, поддерживает ли объект пулы.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
