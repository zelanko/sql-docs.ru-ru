---
title: Выполнение транзакций в ADOMD.NET | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: adomd
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 872d7aca21569018180e537c635032a9d036e3dd
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
  
