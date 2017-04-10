---
title: "Сохранение предусмотренного по умолчанию значения параметра конфигурации блокировок | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Лучшие решения [компонент Database Engine]"
ms.assetid: f214f05b-5f0b-4786-b2ad-b8b4b6e58d72
caps.latest.revision: 12
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 12
---
# Сохранение предусмотренного по умолчанию значения параметра конфигурации блокировок
  Это правило проверяет значение параметра конфигурации «locks». Параметр определяет максимальное количество доступных блокировок. Тем самым ограничивается объем памяти, который компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] использует для блокировок. Значение по умолчанию 0 позволяет компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)] выделять и освобождать структуры блокировок динамически в соответствии с изменяющимися требования к системе.  
  
 Если значение параметра отлично от нуля, то в случае превышения указанного числа блокировок выполнение пакетных заданий будет остановлено и появится сообщение об ошибке, извещающее о недостатке памяти для блокировок.  
  
## Рекомендации  
 Для присвоения параметру конфигурации «locks» значения по умолчанию используется системная хранимая процедура sp_configure в следующей инструкции:  
  
```  
EXEC sp_configure 'locks', 0;  
```  
  
## Дополнительные сведения см. в разделе  
 [Настройка параметра конфигурации сервера locks](../../database-engine/configure-windows/configure-the-locks-server-configuration-option.md)  
  
 [sys.dm_tran_locks (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)  
  
 [sys.dm_os_wait_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)  
  
 [Статья 271509 базы знаний Майкрософт](http://go.microsoft.com/fwlink/?linkid=117788)  
  
## См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  