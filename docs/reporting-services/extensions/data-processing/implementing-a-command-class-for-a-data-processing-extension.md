---
title: "Реализация класса Command для модуля обработки данных | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- data processing extensions [Reporting Services], commands
- Command class
- commands [Reporting Services]
ms.assetid: 465ef8d1-c503-407c-8afd-58d620e344ee
caps.latest.revision: 35
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 9e6858a7f5c67508ff30396bb6ec668b908d671f
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="implementing-a-command-class-for-a-data-processing-extension"></a>Реализация класса Command для модуля обработки данных
  **Команда** объекта формулирует запрос и передает в источнике данных. Текст команды может принимать различные синтаксические формы, включая текст и XML-код. Если результаты возвращаются, **команда** объект возвращает результаты в виде **DataReader** объекта.  
  
 Для создания **команда** , реализуйте интерфейс <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand>. Реализуйте <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> метод, чтобы возвратить результирующий набор как **DataReader** объекта. <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> Метод вашей **команда** класс должен включать реализацию, принимающую <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior> перечисления в качестве аргумента. При развертывании модуля обработки данных в конструкторе отчетов следует предусмотреть реализацию, обрабатывающую вариант <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior.SchemaOnly> в методе <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A>. Список полей передается конструктору отчетов с помощью реализации только схемы. **DataReader** объект, возвращаемый <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> метод должен содержать тип и имя описания полей или столбцов в результирующем наборе.  
  
 При необходимости вашей **команда** класс может реализовывать <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>. Этот интерфейс позволяет проанализировать запрос в реализующем классе и возвратить список параметров в запросе. Возможности интерфейса <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> используются только в конструкторе отчетов. После реализации интерфейса <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> пользователи конструктора отчетов получают возможность вводить параметры с помощью приглашения при запуске отчета в режиме предварительного просмотра. Кроме того, можно просмотреть параметры в **параметры** вкладке **набора данных** диалогового окна.  
  
> [!NOTE]  
>  Не следует реализовывать интерфейс <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>, если пользовательский модуль обработки данных не поддерживает параметры.  
  
 Образец **команда** реализации класса см. в разделе [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>См. также:  
 [модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Реализация модуля обработки данных](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Библиотека служб Reporting Services расширения](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
