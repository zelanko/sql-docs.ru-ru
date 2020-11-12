---
title: Интеграция со средой CLR и транзакции | Документация Майкрософт
description: При интеграции со средой CLR и транзакциях System. Transactions и ADO.NET работают вместе для расширения и упрощения использования локальных и распределенных транзакций в управляемых приложениях.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
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
ms.openlocfilehash: bd65fce2f2a2bdf2ce25f4811063f7f9d56d2e15
ms.sourcegitcommit: 36fe62a3ccf34979bfde3e192cfa778505add465
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/11/2020
ms.locfileid: "94521144"
---
# <a name="clr-integration-and-transactions"></a>Интеграция со средой CLR и транзакции
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Пространство имен **System.Transactions** предоставляет новую платформу транзакций, полностью интегрированную с ADO.NET и со средой CLR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . **System. Transactions** и ADO.NET работают вместе для расширения и упрощения использования локальных и распределенных транзакций в управляемых приложениях.  
  
> [!NOTE]  
>  Определяемая пользователем процедура (UDP) среды CLR не может устанавливать соединение с тем же сервером, на котором она запускается (соединение, замкнутое на себя), и выполнить прикрепление в той же транзакции. Если предпринимается такая попытка, то попытка соединения будет заблокирована, а управление не будет передано обратно определяемой пользователем процедуре. Это приведет к ошибке времени ожидания (сообщение 1206) в определяемой пользователем процедуре.  
  
 Дополнительные сведения о транзакциях и платформе .NET Framework см. в разделах «Выполнение транзакций» и «Использование транзакций» пакета SDK для платформы .NET Framework.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Повышение транзакции](../../relational-databases/clr-integration-data-access-transactions/transaction-promotion.md)  
 Содержит описание возможности повысить уровень транзакции и использования этой функции.  
  
 [Доступ к текущей транзакции](../../relational-databases/clr-integration-data-access-transactions/accessing-the-current-transaction.md)  
 Содержит описание получения доступа к транзакции, которая выполняется в данный момент внутрипроцессно на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Использование System.Transactions](../../relational-databases/clr-integration-data-access-transactions/using-system-transactions.md)  
 Описывает использование программного интерфейса **System. Transactions** (API) в управляемом приложении.  
  
 [Время существования транзакций](../../relational-databases/clr-integration-data-access-transactions/transaction-lifetimes.md)  
 Содержит описание различий во времени существования между транзакциями, запущенными в хранимых процедурах [!INCLUDE[tsql](../../includes/tsql-md.md)], и транзакциями, запущенными в приложениях CLR.  
  
## <a name="see-also"></a>См. также:  
 [Доступ к данным из объектов среды CLR для работы с базами данных](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
