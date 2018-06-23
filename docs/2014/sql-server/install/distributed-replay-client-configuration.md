---
title: Конфигурация клиента распределенного воспроизведения | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ccf03e32-6bd9-43c0-b9b6-9fe0d9163339
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 330334330fd27459f19d3746187150e20900bd93
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36100546"
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
  
  