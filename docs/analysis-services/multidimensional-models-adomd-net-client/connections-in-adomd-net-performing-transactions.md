---
title: "Выполнение транзакций в ADOMD.NET | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- transactions [ADOMD.NET]
- ADOMD.NET, transactions
- AdomdTransaction object
ms.assetid: 7978c28b-c255-43c0-ad05-f38604d4d8fe
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7491ab2b49dd08b0ed1fab4f8f645cd0ac0c66eb
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="connections-in-adomdnet---performing-transactions"></a>Connections in ADOMD.NET - выполнение транзакций
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]В ADOMD.NET, используется <xref:Microsoft.AnalysisServices.AdomdClient.AdomdTransaction> объект для управления контекстом транзакции для данного <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> объекта. Эта функциональность позволяет выполнять несколько команд в одном контексте. Каждая команда читает одни и те же данные, при этом сами эти данные между выполнением каждой команды не изменяются.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Установление соединений в ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/connections-in-adomd-net.md)   
 [Программирование клиента ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/adomd-net-client-programming.md)  
  
  
