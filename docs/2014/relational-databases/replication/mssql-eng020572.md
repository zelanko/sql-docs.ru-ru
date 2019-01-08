---
title: MSSQL_ENG020572 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020572 error
ms.assetid: 636566db-ffcf-4109-8c11-15b8c7cb9cd9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 243b9b1658e2a0b34626e973799127b19ddc0e11
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52806746"
---
# <a name="mssqleng020572"></a>MSSQL_ENG020572
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|20572|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Подписка подписчика "%s" на статью "%s" в публикации "%s" повторно инициализирована после ошибки при проверке.|  
  
## <a name="explanation"></a>Объяснение  
 Было проверено соответствие данных на подписчике данным на издателе, данные не совпали; таким образом, проверка завершилась неуспешно. При включении проверки был выбран параметр, указывающий, что в случае ошибки проверки подписка должна быть повторно инициализирована. Повторная инициализация подписки включает применение нового моментального снимка на подписчике. Дополнительные сведения о проверке см. в разделе [Validate Replicated Data](validate-replicated-data.md).  
  
## <a name="user-action"></a>Действие пользователя  
 После применения нового моментального снимка на подписчике данные на издателе и подписчике будут соответствовать друг другу.  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и событиям (репликация)](errors-and-events-reference-replication.md)  
  
  
