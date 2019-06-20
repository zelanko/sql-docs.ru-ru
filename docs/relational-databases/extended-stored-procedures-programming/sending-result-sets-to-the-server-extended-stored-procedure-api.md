---
title: Отправка результирующих наборов на сервер (расширенный набор API-Интерфейс хранимых процедур) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], sending result sets
- result sets [SQL Server], extended stored procedures
ms.assetid: 9d54673d-ea9d-4ac6-825a-f216ad8b0e34
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: ab77fa15bb4d3d1e68b8335a1c9026b1831a8619
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62742120"
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a>Отправка результирующих наборов на сервер (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Пользуйтесь вместо этого интеграцией со средой CLR.  
  
 При отправке результирующего набора для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], расширенная хранимая процедура должна вызвать соответствующий API следующим образом:  
  
-   **Srv_sendmsg** функция может быть вызвана в любом порядке, до или после были отправлены все строки (если таковые имеются) при помощи **srv_sendrow**. Все сообщения должны быть отправлены клиенту, перед отправкой состояние завершения с **srv_senddone**.  
  
-   Функция **srv_sendrow** вызывается по разу для каждой из строк, отправляемых клиенту. Все строки должны быть отправлены клиенту до любого сообщения, значения состояния или состояние завершения отправляются с **srv_sendmsg**, **srv_status** аргумент **srv_pfield**, или **srv_senddone**.  
  
-   Отправке строки, для которой не все столбцы определены с помощью **srv_describe** заставляет приложение выдаст информационное сообщение об ошибке и вернет клиенту значение FAIL. В этом случае строка не отправляется.  
  
## <a name="see-also"></a>См. также  
 [Создание расширенных хранимых процедур](../../relational-databases/extended-stored-procedures-programming/creating-extended-stored-procedures.md)  
  
  
