---
title: Отключение и повторное подключение набора записей | Документы Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset object [ADO], disconnecting and reconnecting
ms.assetid: c5134af7-81d6-4de4-9fd1-cfe29973545e
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c8a3f26ec756ac328c7b717f5f25b566d543d0ff
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="disconnecting-and-reconnecting-the-recordset"></a>Отключение и повторное подключение набора записей
Одним из самых мощных функциональных возможностей в ADO является возможность открыть набор записей для клиентского источника данных, а затем отключиться набора записей из источника данных. После отключения набора записей, соединение с источником данных может быть закрыта, тем самым освобождению ресурсов на сервере, используемом для его обслуживания. Можно продолжить просмотр и изменение данных в наборе записей, пока он отключен и последующего повторного подключения к источнику данных и отправка обновлений в пакетном режиме.  
  
 Чтобы отключить набор записей, откройте его с adUseClient положения курсора и установите для свойства ActiveConnection значение Nothing. (Пользователи C++ следует задать ActiveConnection равно NULL для отключения.)  
  
 Мы будем использовать отключенный набор записей позже в этом разделе при обсуждении постоянного хранения набора записей для решения проблемы, в котором должен быть данные в наборе записей, доступных приложению, пока клиентский компьютер не подключен к сети.  
  
## <a name="see-also"></a>См. также  
 [Пакетный режим](../../../ado/guide/data/batch-mode.md)
