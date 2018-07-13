---
title: Выполнение транзакций в ADOMD.NET | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- transactions [ADOMD.NET]
- ADOMD.NET, transactions
- AdomdTransaction object
ms.assetid: 7978c28b-c255-43c0-ad05-f38604d4d8fe
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 04157786e3a3d9349c2f1e324291a3a0bda5928d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37167601"
---
# <a name="performing-transactions-in-adomdnet"></a>Выполнение транзакций в ADOMD.NET
  Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> используется в ADOMD.NET для управления контекстом транзакции для данного объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>. Эта функциональность позволяет выполнять несколько команд в одном контексте. Каждая команда читает одни и те же данные, при этом сами эти данные между выполнением каждой команды не изменяются.  
  
> [!NOTE]  
>  Класс <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> является реализацией интерфейса `System.Data.IDbTransaction`, частью библиотеки классов платформы [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework и реализуется всеми поставщиками данных платформы .NET Framework, поддерживающими транзакции.  
  
 Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> поддерживает только транзакции READ COMMITTED, в которых во время чтения данных устанавливаются совмещаемые блокировки для предотвращения чтения «грязных» данных.  
  
 Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> используется для запуска транзакции. После запуска транзакции команды, для которых требуется использовать эту транзакцию, выполняются по соединению, которое ее запустило. После завершения использования транзакции для нее можно либо выполнить откат, либо зафиксировать.  
  
## <a name="starting-a-transaction"></a>Запуск транзакции  
 Экземпляр объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> создается путем вызова метода <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.BeginTransaction%2A> объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>. Следующий пример демонстрирует, как создать экземпляр объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction>.  
  
```  
Dim objTransaction As AdomdTransaction = objConnection.BeginTransaction()  
AdomdTransaction objTransaction = objConnection.BeginTransaction();  
```  
  
## <a name="rolling-back-a-transaction"></a>Откат транзакции  
 Чтобы можно было выполнить откат существующей, незавершенной транзакции, вызывается метод <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction.Rollback%2A> объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction>. При вызове этого метода для существующей, завершенной транзакции возникает исключение.  
  
## <a name="committing-a-transaction"></a>Фиксация транзакции  
 После того как метод <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.BeginTransaction%2A> был вызван для запуска транзакции, чтобы завершить эту транзакцию, необходимо вызвать метод <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction.Commit%2A> объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction>. При вызове этого метода для существующей, завершенной транзакции возникает исключение.  
  
## <a name="see-also"></a>См. также  
 [Установление соединений в ADOMD.NET](connections-in-adomd-net.md)   
 [Программирование клиента ADOMD.NET](adomd-net-client-programming.md)  
  
  
