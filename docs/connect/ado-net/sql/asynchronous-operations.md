---
title: Асинхронные операции
description: Описание выполнения асинхронных операций с базой данных при помощи API-интерфейса, который создан по асинхронной модели, используемой платформой .NET Framework.
ms.date: 09/30/2019
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 79cde936328476408fabb3df7a6bff8d983ace1c
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452321"
---
# <a name="asynchronous-operations"></a>Асинхронные операции

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Некоторые операции с базой данных, например выполнение команд, могут занять значительное время. В этом случае приложения, работающие с одним потоком, должны блокировать другие операции и дожидаться завершения команды, прежде чем они смогут продолжить выполнение собственных операций. В противоположность этому при назначении длительной операции в фоновый поток основной поток может оставаться активным в течение всей операции. Например, в приложении Windows делегирование длительной операции в фоновый поток позволяет потоку пользовательского интерфейса оставаться в рабочем процессе во время выполнения операции.  
  
Платформа .NET предоставляет несколько стандартных шаблонов асинхронного проектирования, которые разработчики могут использовать для использования преимуществ фоновых потоков и освобождения пользовательского интерфейса или потоков с высоким приоритетом для выполнения других операций в своем <xref:Microsoft.Data.SqlClient.SqlCommand>ном классе. В частности, методы <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteReader%2A> и <xref:Microsoft.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A>, связанные с методами <xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>, <xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteReader%2A> и <xref:Microsoft.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A>, обеспечивают асинхронную поддержку.  
  
> [!NOTE]
>  Асинхронное программирование — это основная функция .NET. Дополнительные сведения о различных асинхронных методах, доступных разработчикам, см. в разделе [асинхронный вызов синхронных методов](https://docs.microsoft.com/dotnet/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously).  
  
Несмотря на то, что использование асинхронных методов с ADO.NET-функциями не добавляет никаких особых соображений, важно помнить о преимуществах и ловушках создания многопоточных приложений. В примерах, приведенных в этом разделе, указываются некоторые важные проблемы, которые необходимо учитывать при создании приложений с многопоточной функциональностью.  
  
## <a name="in-this-section"></a>В этом разделе  
[Приложения для Windows, использующие обратные вызовы](windows-applications-callbacks.md)  
Содержит пример, демонстрирующий безопасное выполнение асинхронной команды с правильной обработкой взаимодействия с формой и ее содержимым из отдельного потока.  
  
[Приложения ASP.NET, использующие дескрипторы ожидания](aspnet-apps-use-wait-handles.md)  
Содержит пример, демонстрирующий выполнение нескольких параллельных команд на странице ASP.NET с использованием дескрипторов ожидания для управления операцией после завершения всех команд.  
  
[Выполнение опросов в консольных приложениях](poll-console-applications.md)  
Содержит пример, демонстрирующий использование опроса для ожидания завершения асинхронного выполнения команды из консольного приложения. Этот метод также является допустимым в библиотеке классов или другом приложении без пользовательского интерфейса.  
  
## <a name="next-steps"></a>Дальнейшие действия
- [SQL Server и ADO.NET](index.md)
- [Асинхронный вызов синхронных методов](https://docs.microsoft.com/dotnet/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously)
