---
description: Метод setResponseBuffering (SQLServerDataSource)
title: Метод setResponseBuffering (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setResponseBuffering(String responseBufferingValue)
apilocation:
- SQLServerDataSource.setResponseBuffering(String responseBufferingValue)
apitype: Assembly
ms.assetid: c9e43ff2-8117-4dca-982d-83c863d0c8e1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 90f66ec23ebd40296e5dee45bb3c663688551cc1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88458424"
---
# <a name="setresponsebuffering-method-sqlserverdatasource"></a>Метод setResponseBuffering (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает режим буферизации ответа для подключений, созданных с использованием этого объекта [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setResponseBuffering(java.lang.String value)  
```  
  
#### <a name="parameters"></a>Параметры  
 *value*  
  
 Объект **String**, содержащий режим буферизации и потоковой передачи. Допустимый режим может быть одной из следующих строк без учета регистра: **full** или **adaptive**.  
  
## <a name="remarks"></a>Remarks  
 Значение **full** указывает на чтение всех результатов с сервера во время выполнения.  
  
 Значение **adaptive** указывает на буферизацию минимального количества данных при необходимости. Значение **adaptive** — это режим буферизации по умолчанию.  
  
 Дополнительные сведения об использовании режима буферизации ответов см. в статье [Использование адаптивной буферизации](../../../connect/jdbc/using-adaptive-buffering.md).  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
