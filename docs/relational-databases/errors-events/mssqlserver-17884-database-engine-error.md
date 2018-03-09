---
title: "MSSQLSERVER_17884 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 17884 (Database Engine error)
ms.assetid: 8d05ba05-3f71-4dc3-bd81-2ea5ac9fe843
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1311779c5ff5bc452c92654231aafc3ce543de84
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver17884"></a>MSSQLSERVER_17884
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17884|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SRV_SCHEDULER_DEADLOCK|  
|Текст сообщения|Новые запросы, предназначенные для обработки на узле %d, не приняты рабочим потоком в течение %d секунд. Это может быть вызвано блокирующими или долго выполняющимися запросами, которые увеличивают время ответа клиента. При помощи параметра конфигурации max worker threads увеличьте число допустимых потоков либо оптимизируйте запросы, выполняемые в настоящее время.  Эффективность использования процесса SQL: %d%%. Бездействие системы %d%%.|  
  
## <a name="explanation"></a>Объяснение  
Ни один из планировщиков не подает признаков выполнения. Это может быть вызвано взаимоблокировкой, при которой ни один поток не может продолжать работу и ни одно новое задание не может быть принято и обработано. Если эффективность процесса низкая, то возможно, что другие процессы, выполняемые на том же компьютере, вызывают нехватку ресурсов ЦП для серверного процесса.  
  
## <a name="user-action"></a>Действие пользователя  
Определите причину блокировки и остановки выполнения. Устраните найденные проблемы. Если эффективность процесса низкая, проверьте, какую нагрузку на систему создают другие процессы.  
  
