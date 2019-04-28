---
title: Параметры конфигурации сервера "access check cache" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- access check cache option
ms.assetid: 0a992ea8-3ec6-4a4d-97b5-460ae7326247
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a82aa2872f5a1e1658ab3d736c2651253bb7cc74
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812047"
---
# <a name="access-check-cache-server-configuration-options"></a>Параметры конфигурации сервера «access check cache»
  При доступе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]к объектам базы данных проверка доступа кэшируется во внутренней структуре, которую называют **кэшем результатов проверки доступа**. Параметры **access check cache quota** и **access check cache bucket count** управляют количеством записей и числом сегментов хэша, которые используются в **кэше результатов проверки доступа**. В редких случаях можно добиться увеличения производительности, изменив эти параметры.  
  
 Значение по умолчанию 0 указывает на то, что этими параметрами управляет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Майкрософт рекомендует изменять эти параметры только под руководством службы поддержки пользователей Майкрософт.  
  
## <a name="see-also"></a>См. также  
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
