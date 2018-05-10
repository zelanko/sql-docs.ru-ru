---
title: Принудительный запуск службы в сеансе зеркального отображения базы данных (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: high-availability
ms.component: database-mirroring
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- forced service [SQL Server]
- database mirroring [SQL Server], forcing service
ms.assetid: 8b6ffe77-35f3-4e2a-a658-8a38a8e1c794
caps.latest.revision: 40
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3268d41ca0acac9c41e7e688ac4d036b56aa26c0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="force-service-in-a-database-mirroring-session-transact-sql"></a>Принудительный запуск службы в сеансе зеркального отображения базы данных (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Если в режимах с высокой производительностью и высокой безопасностью без автоматической отработки отказа на основном сервере происходит сбой, в то время как доступен зеркальный сервер, владелец базы данных может сделать базу данных доступной, принудительно переведя ее на другой ресурс (с возможной потерей данных). Этот параметр доступен только при выполнении следующих условий:  
  
-   основной сервер недоступен;  
  
-   параметр WITNESS установлен в OFF или подключен к зеркальному серверу.  
  
> [!CAUTION]  
>  Метод принудительного обслуживания применяется исключительно при аварийном восстановлении. Принудительный запуск службы может привести к потере некоторых данных. Поэтому используйте принудительный запуск службы только в случае, когда потеря некоторых данных допустима, чтобы восстановить службу базы данных немедленно. Если это вызовет риск потери значительного объема данных, рекомендуется остановить зеркальное отображение и вручную повторно синхронизировать базы данных. Дополнительные сведения о рисках принудительного обслуживания см. в разделе [Database Mirroring Operating Modes](../../database-engine/database-mirroring/database-mirroring-operating-modes.md).  
  
 Принудительное обслуживание приостанавливает сеанс и создает новую вилку восстановления. Оно вызывает такой же эффект, как и удаление зеркального отображения с восстановлением бывшей основной базы данных. Тем не менее, принудительное обслуживание облегчает повторную синхронизацию базы данных (с возможной потерей данных) при возобновлении зеркального отображения.  
  
### <a name="to-force-service-in-a-database-mirroring-session"></a>Принудительный запуск службы в сеансе зеркального отображения базы данных  
  
1.  Установите соединение с зеркальным сервером.  
  
2.  Выполните следующую инструкцию:  
  
     ALTER DATABASE *<имя_базы_данных>* SET PARTNER FORCE_SERVICE_ALLOW_DATA_LOSS  
  
     где *<имя_базы_данных>*  — зеркально отображаемая база данных.  
  
     Зеркальный сервер немедленно переходит на основной сервер, а зеркальное отображение приостанавливается.  
  
## <a name="see-also"></a>См. также:  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [Database Mirroring Operating Modes](../../database-engine/database-mirroring/database-mirroring-operating-modes.md)  
  
  
