---
title: "Выполнение транзакций в ADOMD.NET | Документы Microsoft"
ms.custom: 
ms.date: 02/14/2018
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- transactions [ADOMD.NET]
- ADOMD.NET, transactions
- AdomdTransaction object
ms.assetid: 7978c28b-c255-43c0-ad05-f38604d4d8fe
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 76964d9623a5ca477e2cc718d71739f4c69cdb1b
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="connections-in-adomdnet---performing-transactions"></a>Connections in ADOMD.NET - выполнение транзакций
  Объект <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> используется в ADOMD.NET для управления контекстом транзакции для данного объекта <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection>. Эта функциональность позволяет выполнять несколько команд в одном контексте. Каждая команда читает одни и те же данные, при этом сами эти данные между выполнением каждой команды не изменяются.  
  
> [!NOTE]  
>  <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> Класс — это реализация **System.Data.IDbTransaction** интерфейс часть [!INCLUDE[msCoName](../../includes/msconame-md.md)] библиотеки классов .NET Framework и реализуется всеми поставщиками данных .NET Framework, поддерживающие транзакции.  
  
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
 [Установление соединений в ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net.md)   
 [Программирование клиента ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)  
  
  
