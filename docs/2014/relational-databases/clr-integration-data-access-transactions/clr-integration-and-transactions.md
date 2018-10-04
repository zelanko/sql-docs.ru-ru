---
title: Интеграция со средой CLR и транзакции | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- managed code [SQL Server], transactions
- common language runtime [SQL Server], transactions
- System.Transactions namespace
- transactions [CLR integration]
ms.assetid: 381d206e-06e2-48d0-8206-295fcf06ac98
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c6d1b302d6ed0f35ce6fcb60e0afb90415c21d1e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48130484"
---
# <a name="clr-integration-and-transactions"></a>Интеграция со средой CLR и транзакции
  Пространство имен `System.Transactions` предоставляет новую платформу транзакций, полностью интегрированную с ADO.NET и со средой CLR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Совместное использование пространства имен `System.Transactions` и ADO.NET позволяет расширить и упростить использование локальных и распределенных транзакций в управляемых приложениях.  
  
> [!NOTE]  
>  Определяемая пользователем процедура (UDP) среды CLR не может устанавливать соединение с тем же сервером, на котором она запускается (соединение, замкнутое на себя), и выполнить прикрепление в той же транзакции. Если предпринимается такая попытка, то попытка соединения будет заблокирована, а управление не будет передано обратно определяемой пользователем процедуре. Это приведет к ошибке времени ожидания (сообщение 1206) в определяемой пользователем процедуре.  
  
 Дополнительные сведения о транзакциях и платформе .NET Framework см. в разделах «Выполнение транзакций» и «Использование транзакций» пакета SDK для платформы .NET Framework.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Повышение транзакции](transaction-promotion.md)  
 Содержит описание возможности повысить уровень транзакции и использования этой функции.  
  
 [Доступ к текущей транзакции](accessing-the-current-transaction.md)  
 Содержит описание получения доступа к транзакции, которая выполняется в данный момент внутрипроцессно на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Использование System.Transactions](../native-client-ole-db-transactions/transactions.md)  
 Содержит описание использования прикладного программного интерфейса (API) `System.Transactions` в управляемом приложении.  
  
 [Время существования транзакций](transaction-lifetimes.md)  
 Содержит описание различий во времени существования между транзакциями, запущенными в хранимых процедурах [!INCLUDE[tsql](../../includes/tsql-md.md)], и транзакциями, запущенными в приложениях CLR.  
  
## <a name="see-also"></a>См. также  
 [Доступ к данным из объектов среды CLR для работы с базами данных](../clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
