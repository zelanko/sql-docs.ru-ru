---
title: Реализация класса Command для модуля обработки данных | Документы Майкрософт
description: Узнайте, как реализовать класс Command для модуля обработки данных, чтобы модуль мог формулировать запросы и передавать их в источник данных.
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
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 7150b14354be738baa8a127cfe7025dc3245b03e
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84529523"
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
  
  
