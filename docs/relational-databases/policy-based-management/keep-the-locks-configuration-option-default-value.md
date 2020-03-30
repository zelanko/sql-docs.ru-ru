---
title: Сохранение предусмотренного по умолчанию значения для параметра конфигурации блокировок | Документация Майкрософт
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: f214f05b-5f0b-4786-b2ad-b8b4b6e58d72
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 57647a5ddd5f5bb98095f951d3fd3522757e0616
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68087132"
---
# <a name="keep-the-locks-configuration-option-default-value"></a>Сохранение предусмотренного по умолчанию значения параметра конфигурации блокировок
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Это правило проверяет значение параметра конфигурации «locks». Параметр определяет максимальное количество доступных блокировок. Тем самым ограничивается объем памяти, который компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] использует для блокировок. Значение по умолчанию 0 позволяет компоненту [!INCLUDE[ssDE](../../includes/ssde-md.md)] выделять и освобождать структуры блокировок динамически в соответствии с изменяющимися требования к системе.  
  
 Если значение параметра отлично от нуля, то в случае превышения указанного числа блокировок выполнение пакетных заданий будет остановлено и появится сообщение об ошибке, извещающее о недостатке памяти для блокировок.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Для присвоения параметру конфигурации «locks» значения по умолчанию используется системная хранимая процедура sp_configure в следующей инструкции:  
  
```  
EXEC sp_configure 'locks', 0;  
```  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Настройка параметра конфигурации сервера locks](../../database-engine/configure-windows/configure-the-locks-server-configuration-option.md)  
  
 [sys.dm_tran_locks (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-tran-locks-transact-sql.md)  
  
 [sys.dm_os_wait_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)  
  
 [Статья 271509 базы знаний Майкрософт](https://go.microsoft.com/fwlink/?linkid=117788)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
