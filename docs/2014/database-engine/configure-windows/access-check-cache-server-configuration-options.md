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
ms.openlocfilehash: 8f05e2a9bfd2cacfcbeb6128411f7d10c531600e
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935985"
---
# <a name="access-check-cache-server-configuration-options"></a>Параметры конфигурации сервера «access check cache»
  При доступе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]к объектам базы данных проверка доступа кэшируется во внутренней структуре, которую называют **кэшем результатов проверки доступа**. Параметры **access check cache quota** и **access check cache bucket count** управляют количеством записей и числом сегментов хэша, которые используются в **кэше результатов проверки доступа**. В редких случаях можно добиться увеличения производительности, изменив эти параметры.  
  
 Значение по умолчанию 0 указывает на то, что этими параметрами управляет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Майкрософт рекомендует изменять эти параметры только под руководством службы поддержки пользователей Майкрософт.  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
