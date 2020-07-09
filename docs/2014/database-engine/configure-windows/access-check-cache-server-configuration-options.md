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
- access check cache bucket count
- access check cache quota
ms.assetid: 0a992ea8-3ec6-4a4d-97b5-460ae7326247
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: feed895eeb7b11b4c41c51c4c26859a1057d2733
ms.sourcegitcommit: 21c14308b1531e19b95c811ed11b37b9cf696d19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2020
ms.locfileid: "86158762"
---
# <a name="access-check-cache-server-configuration-options"></a>Параметры конфигурации сервера «access check cache»
При доступе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]к объектам базы данных проверка доступа кэшируется во внутренней структуре, которую называют **кэшем результатов проверки доступа**. 
  
Параметр **доступ к счетчику контейнеров проверки доступа** определяет количество сегментов хэша, используемых для кэша результатов проверки доступа. 

Параметр **доступа к квоте проверки кэша** определяет количество записей, хранящихся в кэше результатов проверки доступа. При достижении максимального числа записей самые старые записи удаляются из кэша результатов проверки доступа.
  
Значение по умолчанию 0 указывает на то, что этими параметрами управляет [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Из [!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)] до [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] значения по умолчанию преобразуются в следующие внутренние конфигурации:
-   Для доступа к числу контейнеров проверки для кэша значение 0 задает значение по умолчанию 256 сегментов для архитектуры x86 и 2 048 для архитектур x64 и IA-64.
-   Для доступа к квоте проверки кэша значение 0 задает значение по умолчанию 1 024 записей для архитектуры x86 и 28 192 048 контейнеров для архитектур x64 и IA-64.

В редких случаях можно добиться увеличения производительности, изменив эти параметры. Например, может потребоваться уменьшить размер кэша результатов проверки доступа, если используется слишком много памяти. Также может потребоваться увеличить размер кэша результатов проверки доступа, если при пересчете разрешений используется высокая загрузка ЦП.

> [!IMPORTANT]
> Майкрософт рекомендует изменять эти параметры только под руководством службы поддержки пользователей Майкрософт.
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
