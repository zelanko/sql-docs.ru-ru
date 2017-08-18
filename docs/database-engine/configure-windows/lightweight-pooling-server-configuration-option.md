---
title: "Параметр конфигурации сервера \"lightweight pooling\" | Документы Майкрософт"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 31
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c82f1c64430cd45299b9378f86c6670841de2707
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="lightweight-pooling-server-configuration-option"></a>Параметр конфигурации сервера «использование упрощенных пулов»
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Чтобы обеспечить уменьшение системных издержек, связанных с излишним переключением контекста, что иногда случается при симметричной многопроцессорной обработке, воспользуйтесь параметром **lightweight pooling** . В случае, когда наблюдается излишнее переключение контекста, использование упрощенных пулов, может обеспечить лучшую производительность за счет встроенного переключения контекстов, помогая таким образом уменьшить количество переходов пользователь/ядро.  
  
 Режим волокон предназначен для ситуаций, когда главным фактором, ограничивающим производительность, является переключение контекста рабочих потоков UMS. Поскольку такая ситуация является нестандартной, использование режима волокон редко увеличивает производительность или масштабируемость типичной системы. Улучшенное переключение контекста в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] также снижает потребность в режиме волокон. Использовать планирование в режиме волокон для выполнения распространенных операций не рекомендуется. Это может привести к снижению производительности, мешая нормальной работе переключения контекста. Кроме того, некоторые компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые используют локальное хранилище потоков (TLS) или объекты, принадлежащие потокам, такие как мьютексы (тип объекта ядра Win32), не выполняются правильно в режиме волокон.  
  
 Значение параметра **использование упрощенных пулов** , равное 1, приводит к переключению [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на расписание режима волокон. Значение этого свойства по умолчанию равно 0.  
  
 Параметр **использование упрощенных пулов** является дополнительным. При вызове системной хранимой процедуры **sp_configure** параметр **lightweight pooling** может быть изменен только в том случае, если параметр **show advanced options** установлен равным 1. Установка параметра вступает в силу после перезапуска сервера.  
  
> [!NOTE]  
>  Использование упрощенных пулов не поддерживается операционными системами [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 и [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows XP. [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] обеспечивает полную поддержку использования упрощенных пулов.  
  
> [!NOTE]  
>  Выполнение в среде CLR не поддерживается при использовании упрощенных пулов. Отключите один из двух параметров: clr enabled или lightweight pooling. Функции, зависящие от среды CLR и неправильно работающие в режиме волокон, включают иерархический тип данных, репликацию и управление на основе политик.  
  
## <a name="see-also"></a>См. также:  
 [Параметр конфигурации сервера «clr enabled»](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [Параметр конфигурации сервера «clr enabled»](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)  
  
  

