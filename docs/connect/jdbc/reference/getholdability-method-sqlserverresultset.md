---
description: Метод getHoldability (SQLServerResultSet)
title: Метод getHoldability (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4508d90f-c3c4-4eac-8001-fb0b93b66734
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fa94ee80f73dfcc21f519d62c4f29f2bda6b3eb2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435896"
---
# <a name="getholdability-method-sqlserverresultset"></a>Метод getHoldability (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение удержания этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getHoldability()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int**, содержащее один из следующих уровней возможности ожидания:  
  
 HOLD_CURSORS_OVER_COMMIT  
  
 CLOSE_CURSORS_AT_COMMIT  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getHoldability определен с помощью метода getHoldability в интерфейсе java.sql.ResultSet.  
  
 Чтобы задать возможность ожидания для результирующего набора, приложения могут использовать метод [setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md) класса [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md). После вызова метода [setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md), создания объекта инструкции и объекта результирующего набора и выполнения инструкции приложению может потребоваться повторное изменение возможности ожидания.  
  
 Для серверных курсоров при соединении с SQL Server 2005 или более поздней версии параметр возможности сохранения влияет только на новые результирующие наборы, которые будут созданы для этого соединения. Однако для SQL Server 2000 установка возможности сохранения относится и к существующим результирующим наборам, и к новым, которые пока не созданы для данного соединения.  
  
 При сбросе уровня удержания и вызове метода getHoldability для ранее созданного объекта результирующего набора возвращенное этим методом значение может отличаться от значения уровня удержания, возвращенного следующими методами: Statement.getResultSetHoldability, Connection.getHoldability и DatabaseMetaData.getResultSetHoldability.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
