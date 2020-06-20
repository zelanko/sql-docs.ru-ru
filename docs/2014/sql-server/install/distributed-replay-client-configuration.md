---
title: Конфигурация клиента распределенное воспроизведение | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ccf03e32-6bd9-43c0-b9b6-9fe0d9163339
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 72336f2f012ad6f2da03440f431d2fe5be294b07
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85012706"
---
# <a name="distributed-replay-client-configuration"></a>Конфигурация клиента распределенного воспроизведения
  Страница **Конфигурация клиента распределенного воспроизведения** мастера установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет указать пользователей, которым нужно предоставить административные разрешения на службу клиента распределенного воспроизведения.  
  
 Пользователи с административными разрешениями будут иметь неограниченный доступ к службе клиента распределенного воспроизведения.  
  
## <a name="options"></a>Варианты  
 **Имя контроллера**  
 Это необязательный параметр, значение по умолчанию — \<*blank*> .  
  
 Введите имя контроллера, с которым будет связываться клиентский компьютер для доступа к службе клиента распределенного воспроизведения. Следует отметить следующее.  
  
-   Должно быть указано полное доменное имя (FQDN). Например, FQDN узла с именем server1 в иерархии продуктов Майкрософт может иметь вид server1.products.microsoft.com.  
  
-   Если контроллер уже настроен, введите имя этого контроллера при настройке каждого клиента.  
  
-   Если контроллер еще не настроен, имя контроллера можно оставить пустым. Однако необходимо вручную ввести имя контроллера в файл **конфигурации клиента** .  
  
 **Рабочий каталог**  
 Укажите рабочий каталог для службы клиента распределенного воспроизведения.  
  
 Рабочий каталог по умолчанию \<*drive letter*> : \Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \DReplayClient\WorkingDir \\ .  
  
 **Папка результатов**  
 Укажите каталог результатов для службы клиента распределенного воспроизведения.  
  
 Каталог результатов по умолчанию \<*drive letter*> : \Program Files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \DReplayClient\ResultDir \\ .  
  
  
