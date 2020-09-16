---
description: Метод getResponseBuffering (SQLServerDataSource)
title: Метод getResponseBuffering (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getResponseBuffering()
apilocation:
- SQLServerDataSource.getResponseBuffering()
apitype: Assembly
ms.assetid: 19585a93-88a4-415e-a20e-12ba58cddeaa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 387f5442224f26095b0803891725ab8af81996ef
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434806"
---
# <a name="getresponsebuffering-method-sqlserverdatasource"></a>Метод getResponseBuffering (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает режим буферизации ответов для этого объекта [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getResponseBuffering()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Строка** со значением **full** или **adaptive** в нижнем регистре.  
  
## <a name="remarks"></a>Remarks  
 Значение **full** указывает на чтение всех результатов с сервера во время выполнения.  
  
 Значение **adaptive** указывает на буферизацию минимального количества данных при необходимости. Значение **adaptive** — это режим буферизации по умолчанию.  
  
 Дополнительные сведения об использовании режима буферизации ответов см. в статье [Использование адаптивной буферизации](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод setResponseBuffering (SQLServerDataSource)](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md)   
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
