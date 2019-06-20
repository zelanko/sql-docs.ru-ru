---
title: Отключение и повторное подключение набора записей | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset object [ADO], disconnecting and reconnecting
ms.assetid: c5134af7-81d6-4de4-9fd1-cfe29973545e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a263903ab4f51d583b6533b6802fabd6c888f479
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66700786"
---
# <a name="disconnecting-and-reconnecting-the-recordset"></a>Отключение и повторное подключение набора записей
Одним из наиболее мощных функций, находящихся в ADO является возможность открыть набор записей на стороне клиента из источника данных, а затем отключиться набор записей из источника данных. После отключения набор записей, подключение к источнику данных можно закрыть, тем самым освобождению ресурсов на сервере, используемом для его обслуживания. Можно просматривать и редактировать данные в наборе записей, пока устройство не подключено и последующего повторного подключения к источнику данных и отправка обновлений в пакетном режиме.  
  
 Чтобы отключить набор записей, откройте его в расположении курсора adUseClient и затем присвойте свойству ActiveConnection равно Nothing. (C++ следует выбирать ActiveConnection равным NULL, чтобы отключить.)  
  
 Мы будем использовать несвязанный набор записей позже в этом разделе при обсуждении сохраняемости набора записей для решения проблемы, в котором необходимо иметь данные в наборе записей, доступные для приложения, а клиентский компьютер не подключен к сети.  
  
## <a name="see-also"></a>См. также  
 [Пакетный режим](../../../ado/guide/data/batch-mode.md)
