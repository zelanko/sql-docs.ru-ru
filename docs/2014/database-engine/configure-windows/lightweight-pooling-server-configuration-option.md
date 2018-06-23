---
title: Параметр конфигурации сервера "lightweight pooling" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- default lightweight pooling
- decreasing overhead
- lightweight pooling option
- system overhead [SQL Server]
- performance [SQL Server], lightweight pooling
- context switching [SQL Server], lightweight pooling option
- excessive context switching [SQL Server]
- reducing overhead
- overhead [SQL Server]
ms.assetid: 2dc11b61-d065-4126-8e00-acf40390f9fb
caps.latest.revision: 30
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ea0ca3ddcb5666def080779bd91521d59ae6b2c2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098019"
---
# <a name="lightweight-pooling-server-configuration-option"></a>Параметр конфигурации сервера «использование упрощенных пулов»
  Чтобы обеспечить уменьшение системных издержек, связанных с излишним переключением контекста, что иногда случается при симметричной многопроцессорной обработке, воспользуйтесь параметром **lightweight pooling** . В случае, когда наблюдается излишнее переключение контекста, использование упрощенных пулов, может обеспечить лучшую производительность за счет встроенного переключения контекстов, помогая таким образом уменьшить количество переходов пользователь/ядро.  
  
 Режим волокон предназначен для ситуаций, когда главным фактором, ограничивающим производительность, является переключение контекста рабочих потоков UMS. Поскольку такая ситуация является нестандартной, использование режима волокон редко увеличивает производительность или масштабируемость типичной системы. Улучшенное переключение контекста в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] также снижает потребность в режиме волокон. Использовать планирование в режиме волокон для выполнения распространенных операций не рекомендуется. Это может привести к снижению производительности, мешая нормальной работе переключения контекста. Кроме того, некоторые компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые используют локальное хранилище потоков (TLS) или объекты, принадлежащие потокам, такие как мьютексы (тип объекта ядра Win32), не выполняются правильно в режиме волокон.  
  
 Значение параметра **использование упрощенных пулов** , равное 1, приводит к переключению [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на расписание режима волокон. Значение этого свойства по умолчанию равно 0.  
  
 Параметр **использование упрощенных пулов** является дополнительным. При вызове системной хранимой процедуры **sp_configure** параметр **lightweight pooling** может быть изменен только в том случае, если параметр **show advanced options** установлен равным 1. Установка параметра вступает в силу после перезапуска сервера.  
  
> [!NOTE]  
>  Использование упрощенных пулов не поддерживается операционными системами [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 и [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows XP. [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] обеспечивает полную поддержку использования упрощенных пулов.  
  
> [!NOTE]  
>  Выполнение в среде CLR не поддерживается при использовании упрощенных пулов. Отключите один из двух параметров: clr enabled или lightweight pooling. Функции, зависящие от среды CLR и неправильно работающие в режиме волокон, включают иерархический тип данных, репликацию и управление на основе политик.  
  
## <a name="see-also"></a>См. также  
 [Параметр конфигурации сервера «clr enabled»](clr-enabled-server-configuration-option.md)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Параметр конфигурации сервера «clr enabled»](clr-enabled-server-configuration-option.md)  
  
  
