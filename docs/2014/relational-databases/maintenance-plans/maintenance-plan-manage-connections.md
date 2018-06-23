---
title: План обслуживания (управление соединениями) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.maint.connections.f1
ms.assetid: 95ad9375-6584-423e-b9de-0e86782f8017
caps.latest.revision: 13
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 20f9f809f7ac04cd0e4f8c2975e23d42571b0f77
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095677"
---
# <a name="maintenance-plan-manage-connections"></a>План обслуживания (управление соединениями)
  Используйте диалоговое окно **Управление соединениями** , чтобы задать свойства соединений, используемых планами обслуживания. При создании плана обслуживания устанавливается локальное соединение с сервером, на котором создается план. Используйте это соединение, чтобы создать задачи, работающие по данному локальному соединению. При необходимости используйте диалоговое окно **Управление соединениями** , чтобы добавить их. Как только дополнительные соединения будут настроены, они будут появляться в окне соединений для каждой задачи.  
  
## <a name="options"></a>Параметры  
 **Server**  
 Экземпляр сервера.  
  
 **Проверка подлинности**  
 Указывает, используется ли при соединении проверка подлинности Windows или проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Планы обслуживания](maintenance-plans.md)  
  
  