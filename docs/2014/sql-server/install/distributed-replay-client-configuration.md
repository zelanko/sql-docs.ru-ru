---
title: Конфигурация клиента распределенного воспроизведения | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ccf03e32-6bd9-43c0-b9b6-9fe0d9163339
caps.latest.revision: 15
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 83863c8bc5547ec0839eed7e0883de4d22c4f693
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37168145"
---
# <a name="distributed-replay-client-configuration"></a>Конфигурация клиента распределенного воспроизведения
  Страница **Конфигурация клиента распределенного воспроизведения** мастера установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет указать пользователей, которым нужно предоставить административные разрешения на службу клиента распределенного воспроизведения.  
  
 Пользователи с административными разрешениями будут иметь неограниченный доступ к службе клиента распределенного воспроизведения.  
  
## <a name="options"></a>Параметры  
 **Имя контроллера**  
 Это необязательный параметр, и значение по умолчанию — \< *пустой*>.  
  
 Введите имя контроллера, с которым будет связываться клиентский компьютер для доступа к службе клиента распределенного воспроизведения. Следует отметить следующее.  
  
-   Должно быть указано полное доменное имя (FQDN). Например, FQDN узла с именем server1 в иерархии продуктов Майкрософт может иметь вид server1.products.microsoft.com.  
  
-   Если контроллер уже настроен, введите имя этого контроллера при настройке каждого клиента.  
  
-   Если контроллер еще не настроен, имя контроллера можно оставить пустым. Однако необходимо вручную ввести имя контроллера в файл **конфигурации клиента** .  
  
 **Рабочий каталог**  
 Укажите рабочий каталог для службы клиента распределенного воспроизведения.  
  
 Рабочий каталог по умолчанию — \<*буква диска*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\WorkingDir\\.  
  
 **Каталог результатов**  
 Укажите каталог результатов для службы клиента распределенного воспроизведения.  
  
 Каталог результатов по умолчанию — \<*буква диска*>:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\ResultDir\\.  
  
  
