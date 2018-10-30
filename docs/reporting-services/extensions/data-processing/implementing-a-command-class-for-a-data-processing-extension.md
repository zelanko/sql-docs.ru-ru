---
title: Реализация класса Command для модуля обработки данных | Документы Майкрософт
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], commands
- Command class
- commands [Reporting Services]
ms.assetid: 465ef8d1-c503-407c-8afd-58d620e344ee
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2093aad82661133944227dbd0458b66cfb19da94
ms.sourcegitcommit: 3daacc4198918d33179f595ba7cd4ccb2a13b3c0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50028723"
---
# <a name="implementing-a-command-class-for-a-data-processing-extension"></a>Реализация класса Command для модуля обработки данных
  Объект **Command** формулирует запрос и передает его в источник данных. Текст команды может принимать различные синтаксические формы, включая текст и XML-код. При наличии возвращенных результатов объект **Command** возвращает результаты как объект **DataReader**.  
  
 Чтобы создать класс **Command**, реализуйте интерфейс <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand>. Реализуйте метод <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A>, чтобы возвратить результирующий набор в виде объекта **DataReader**. Метод <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A> класса **Command** должен включать реализацию, принимающую в качестве аргумента перечисление <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior>. При развертывании модуля обработки данных в конструкторе отчетов следует предусмотреть реализацию, обрабатывающую вариант <xref:Microsoft.ReportingServices.DataProcessing.CommandBehavior.SchemaOnly> в методе <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A>. Список полей передается конструктору отчетов с помощью реализации только схемы. Объект **DataReader**, возвращенный методом <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand.ExecuteReader%2A>, должен содержать сведения об имени и типе полей или столбцов в результирующем наборе.  
  
 Дополнительно класс **Command** может реализовывать интерфейс <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>. Этот интерфейс позволяет проанализировать запрос в реализующем классе и возвратить список параметров в запросе. Возможности интерфейса <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> используются только в конструкторе отчетов. После реализации интерфейса <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis> пользователи конструктора отчетов получают возможность вводить параметры с помощью приглашения при запуске отчета в режиме предварительного просмотра. Кроме того, параметры можно просматривать на вкладке **Параметры** в диалоговом окне **Набор данных**.  
  
> [!NOTE]  
>  Не следует реализовывать интерфейс <xref:Microsoft.ReportingServices.DataProcessing.IDbCommandAnalysis>, если пользовательский модуль обработки данных не поддерживает параметры.  
  
 Образец реализации класса **Command** см. в разделе [Образцы продуктов служб SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>См. также:  
 [Модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Реализация модуля обработки данных](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Библиотека модулей Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
