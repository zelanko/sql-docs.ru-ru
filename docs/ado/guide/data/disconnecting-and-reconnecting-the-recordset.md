---
title: "Отключение и повторное подключение набора записей | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Recordset object [ADO], disconnecting and reconnecting
ms.assetid: c5134af7-81d6-4de4-9fd1-cfe29973545e
caps.latest.revision: "4"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8d9d1dd91e7ebfb17c0ddc759a0a55d2368efd1e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="disconnecting-and-reconnecting-the-recordset"></a>Отключение и повторное подключение набора записей
Одним из самых мощных функциональных возможностей в ADO является возможность открыть набор записей для клиентского источника данных, а затем отключиться набора записей из источника данных. После отключения набора записей, соединение с источником данных может быть закрыта, тем самым освобождению ресурсов на сервере, используемом для его обслуживания. Можно продолжить просмотр и изменение данных в наборе записей, пока он отключен и последующего повторного подключения к источнику данных и отправка обновлений в пакетном режиме.  
  
 Чтобы отключить набор записей, откройте его с adUseClient положения курсора и установите для свойства ActiveConnection значение Nothing. (Пользователи C++ следует задать ActiveConnection равно NULL для отключения.)  
  
 Мы будем использовать отключенный набор записей позже в этом разделе при обсуждении постоянного хранения набора записей для решения проблемы, в котором должен быть данные в наборе записей, доступных приложению, пока клиентский компьютер не подключен к сети.  
  
## <a name="see-also"></a>См. также:  
 [Пакетный режим](../../../ado/guide/data/batch-mode.md)
