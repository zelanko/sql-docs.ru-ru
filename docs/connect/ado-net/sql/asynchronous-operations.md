---
title: Асинхронные операции
description: Описание выполнения асинхронных операций с базой данных при помощи API-интерфейса, который создан по асинхронной модели, используемой платформой .NET Framework.
ms.date: 09/30/2019
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 4c88a8ccbc242b0fd85c66acfb3539ec260c58dd
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80928939"
---
# <a name="asynchronous-operations"></a>Асинхронные операции

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Некоторые операции баз данных, например выполнение команд, могут занимать значительное количество времени. В таких случаях однопотоковые приложения должны блокировать другие операции и ожидать завершения команды перед возобновлением собственных операций. В противоположность этому при назначении длительной операции в фоновый поток основной поток может оставаться активным в течение всей операции. Например, в приложении Windows делегирование длительной операции в фоновый поток позволяет потоку пользовательского интерфейса оставаться в рабочем процессе во время выполнения операции.  
  
Платформа .NET предоставляет несколько стандартных шаблонов асинхронного проектирования, которые разработчики могут использовать, чтобы воспользоваться преимуществами фоновых потоков и освобождения пользовательского интерфейса или потоков с высоким приоритетом для выполнения других операций в своем классе <xref:Microsoft.Data.SqlClient.SqlCommand>. В частности, методы <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteReader%2A>и <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A>, связанные с методами <xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>, <xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteReader%2A> и <xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A>, обеспечивают асинхронную поддержку.  
  
> [!NOTE]
>  Асинхронное программирование — это основная функция .NET. Дополнительные сведения о разных видах асинхронной техники, доступных разработчикам, см. в статье [Асинхронный вызов синхронных методов](https://docs.microsoft.com/dotnet/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously).  
  
Несмотря на то, что использование асинхронных методов с функциями ADO.NET не добавляет никаких особых соображений, важно помнить о преимуществах создания многопоточных приложений и о их ловушках. В приведенных в этом разделе примерах указываются некоторые важные проблемы, которые необходимо учитывать при создании приложений с многопоточной функциональностью.  
  
## <a name="in-this-section"></a>В этом разделе  
[Приложения для Windows, использующие обратные вызовы](windows-applications-callbacks.md)  
Содержит пример, демонстрирующий безопасное выполнение асинхронной команды с правильной обработкой взаимодействия с формой и ее содержимым из отдельного потока.  
  
[Приложения ASP.NET, использующие дескрипторы ожидания](aspnet-apps-use-wait-handles.md)  
Содержит пример, демонстрирующий, как выполнять несколько одновременных команд со страницы ASP.NET, используя дескрипторы ожидания для управления операцией при завершении всех команд.  
  
[Выполнение опросов в консольных приложениях](poll-console-applications.md)  
Содержит пример, демонстрирующий использование опроса для ожидания завершения выполнения асинхронной команды из консольного приложения. Этот метод также допустимый в библиотеке классов или другом приложении без пользовательского интерфейса.  
  
## <a name="next-steps"></a>Дальнейшие действия
- [SQL Server и ADO.NET](index.md)
- [Асинхронный вызов синхронных методов](https://docs.microsoft.com/dotnet/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously)
