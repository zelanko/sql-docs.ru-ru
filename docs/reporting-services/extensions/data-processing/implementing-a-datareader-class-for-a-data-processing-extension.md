---
title: "Реализация класса DataReader для модуля обработки данных | Документы Microsoft"
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
- data processing extensions [Reporting Services], data readers
- data readers [Reporting Services]
- DataReader class
- read-only data
ms.assetid: 23e286e7-6074-4fbe-be29-203420d6c3d0
caps.latest.revision: 35
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: cfd3a6cb38c59b1810d046839cb3be4f0dc9846a
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="implementing-a-datareader-class-for-a-data-processing-extension"></a>Реализация класса DataReader для модуля обработки данных
  **DataReader** объекта позволяет клиенту получить только для чтения однопроходный поток данных из источника данных. Результаты возвращаются после выполнения запроса и хранятся в сетевом буфере на клиенте, пока не будут запрошены с помощью **чтения** метод **DataReader** класса. Для создания **DataReader** , следует реализовать <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> и при необходимости реализовать <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension>. С помощью **DataReader** объектов позволяет увеличить производительность приложения как путем получения данных, как только они доступны, вместо ожидания возвращения всех результатов запроса, а также (по умолчанию) хранение только одну строку за один раз в памяти, снижения нагрузки на систему.  
  
 После создания экземпляра вашей **команда** создать класс, **DataReader** путем вызова метода **Command.ExecuteReader** для получения строк из источника данных. **DataReader** реализация должна предоставлять две основные возможности: однопроходный доступ к результирующим наборам, полученным при выполнении команды и доступ к типам столбцов, именам и значениям в каждой строке. Клиенты используют **чтения** метод **DataReader** объект для получения строки из результатов запроса.  
  
 В конструкторе отчетов вашей **DataReader** объект используется для получения списка полей, а также данные схемы о результирующем наборе. Это достигается путем реализации **GetName**, **GetValue**, **GetFieldType** и **GetOrdinal** методы <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> интерфейса.  
  
 Экземпляр <xref:Microsoft.ReportingServices.DataProcessing.IDataReaderExtension> позволяет предоставлять конкретные сведения статистической обработки результирующего набора. Образец **DataReader** реализации класса см. в разделе [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="see-also"></a>См. также:  
 [Модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Реализация модуля обработки данных](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Библиотека служб Reporting Services расширения](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

