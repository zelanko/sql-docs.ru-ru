---
title: "Отправка результирующих наборов на сервер (расширенный набор API-Интерфейс хранимых процедур) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], sending result sets
- result sets [SQL Server], extended stored procedures
ms.assetid: 9d54673d-ea9d-4ac6-825a-f216ad8b0e34
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0dd49eba42bd735430bd73f244e76a13c8315806
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a>Отправка результирующих наборов на сервер (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Пользуйтесь вместо этого интеграцией со средой CLR.  
  
 При отправке результирующего набора для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], расширенная хранимая процедура должна вызвать соответствующий API следующим образом:  
  
-   **Srv_sendmsg** функция может быть вызвана в любом порядке, до или после отправки всех строк (если есть) с **srv_sendrow**. Все сообщения должны быть отправлены клиенту перед отправкой состояние завершения с **srv_senddone**.  
  
-   Функция **srv_sendrow** вызывается по разу для каждой из строк, отправляемых клиенту. Все строки должны быть отправлены клиенту до любые сообщения, значения состояния или состояние завершения отправляются с **srv_sendmsg**, **srv_status** аргумент **srv_pfield**, или **srv_senddone**.  
  
-   Отправке строки, для которой не все столбцы определены с **srv_describe** приложение выдаст информационное сообщение об ошибке и вернет клиенту значение FAIL. В этом случае строка не отправляется.  
  
## <a name="see-also"></a>См. также:  
 [Создание расширенных хранимых процедур](../../relational-databases/extended-stored-procedures-programming/creating-extended-stored-procedures.md)  
  
  
