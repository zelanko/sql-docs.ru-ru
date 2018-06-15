---
title: Интеграция со средой CLR и транзакции | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- common language runtime [SQL Server], ADO.NET
- managed code [SQL Server], transactions
- common language runtime [SQL Server], transactions
- System.Transactions namespace
- transactions [CLR integration]
ms.assetid: 381d206e-06e2-48d0-8206-295fcf06ac98
caps.latest.revision: 19
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 9cab6c061f8baac232563b4afe41952da1b4892e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32921559"
---
# <a name="clr-integration-and-transactions"></a>Интеграция со средой CLR и транзакции
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Пространство имен **System.Transactions** предоставляет новую платформу транзакций, полностью интегрированную с ADO.NET и со средой CLR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . **System.Transactions** и ADO.NET работают вместе, чтобы расширить и упростить использование локальных и распределенных транзакций в управляемых приложениях.  
  
> [!NOTE]  
>  Определяемая пользователем процедура (UDP) среды CLR не может устанавливать соединение с тем же сервером, на котором она запускается (соединение, замкнутое на себя), и выполнить прикрепление в той же транзакции. Если предпринимается такая попытка, то попытка соединения будет заблокирована, а управление не будет передано обратно определяемой пользователем процедуре. Это приведет к ошибке времени ожидания (сообщение 1206) в определяемой пользователем процедуре.  
  
 Дополнительные сведения о транзакциях и платформе .NET Framework см. в разделах «Выполнение транзакций» и «Использование транзакций» пакета SDK для платформы .NET Framework.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Повышение транзакции](../../relational-databases/clr-integration-data-access-transactions/transaction-promotion.md)  
 Содержит описание возможности повысить уровень транзакции и использования этой функции.  
  
 [Доступ к текущей транзакции](../../relational-databases/clr-integration-data-access-transactions/accessing-the-current-transaction.md)  
 Содержит описание получения доступа к транзакции, которая выполняется в данный момент внутрипроцессно на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Использование System.Transactions](../../relational-databases/clr-integration-data-access-transactions/using-system-transactions.md)  
 Описывает использование **System.Transactions** интерфейс программирования (API) в управляемом приложении.  
  
 [Время существования транзакций](../../relational-databases/clr-integration-data-access-transactions/transaction-lifetimes.md)  
 Содержит описание различий во времени существования между транзакциями, запущенными в хранимых процедурах [!INCLUDE[tsql](../../includes/tsql-md.md)], и транзакциями, запущенными в приложениях CLR.  
  
## <a name="see-also"></a>См. также  
 [Доступ к данным из объектов среды CLR для работы с базами данных](../../relational-databases/clr-integration/data-access/data-access-from-clr-database-objects.md)  
  
  
