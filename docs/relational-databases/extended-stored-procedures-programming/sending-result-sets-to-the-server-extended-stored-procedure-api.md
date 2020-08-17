---
description: Отправка результирующих наборов на сервер (API-интерфейс расширенных хранимых процедур)
title: Отправка результирующих наборов на сервер (API-интерфейс расширенных хранимых процедур)
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
ms.custom: seo-dt-2019
ms.openlocfilehash: 4747c464956d4c1da804a4bf9182cbb507a45989
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88383140"
---
# <a name="sending-result-sets-to-the-server-extended-stored-procedure-api"></a>Отправка результирующих наборов на сервер (API-интерфейс расширенных хранимых процедур)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Пользуйтесь вместо этого интеграцией со средой CLR.  
  
 При отправке результирующего набора в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Расширенная хранимая процедура должна вызывать соответствующий API следующим образом:  
  
-   Функция **srv_sendmsg** может быть вызвана в любом порядке до или после отправки всех строк (если таковые имеются) с **srv_sendrow**. Все сообщения должны отправляться клиенту перед отправкой состояния завершения с **srv_senddone**.  
  
-   Функция **srv_sendrow** вызывается по разу для каждой из строк, отправляемых клиенту. Все строки должны отправляться клиенту перед отправкой сообщений, значений состояния или состояний завершения с помощью **srv_sendmsg**, **srv_status** аргумента для **SRV_PFIELD**или **srv_senddone**.  
  
-   При отправке строки, в которой не были все столбцы, определенные с помощью **srv_describe** , приложение создает информационное сообщение об ошибке и возвращает клиенту ошибку. В этом случае строка не отправляется.  
  
## <a name="see-also"></a>См. также:  
 [Создание расширенных хранимых процедур](../../relational-databases/extended-stored-procedures-programming/creating-extended-stored-procedures.md)  
  
  
