---
title: "Произошла ошибка при попытке установить соединение | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1b951da1-f62d-43d2-b40b-270a4a9ab92c
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 226842eb86c8eb7d5981407c805e18495dfb2579
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="an-error-occurred-during-an-attempt-to-establish-a-connection"></a>Произошла ошибка при попытке установить соединение
  Эта ошибка возникает во время запроса данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] на сервере, где не установлен компонент [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint. Она также возникает в случае остановки службы SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) или при попытке просмотра данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] предыдущей версии.  
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Область применения|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint|  
|Номер версии продукта|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Причина|Ошибка подключения к данным.|  
|Текст сообщения|При попытке установить соединение с внешним источником данных произошла ошибка. Следующие соединения не удалось обновить: данные [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] .|  
  
## <a name="explanation"></a>Объяснение  
 Службы Excel возвращают эту ошибку во время запроса данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в книге Excel, которая опубликована на сайте SharePoint, при этом в среде SharePoint не установлен сервер [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint, либо служба SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) остановлена.  
  
 Эта ошибка возникает при срезе или фильтрации данных [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , когда обработчик запросов недоступен.  
  
## <a name="user-action"></a>Действие пользователя  
 Установите [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint или переместите книгу [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в среду SharePoint, где установлен экземпляр [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint. Дополнительные сведения см. в разделе [Установка Power Pivot для SharePoint 2010](http://msdn.microsoft.com/en-us/8d47dde7-c941-4280-a934-e2fe3f9a938f).  
  
 Если программное обеспечение установлено, убедитесь, что экземпляр служб SQL Server Analysis Services ([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) запущен. Установите флажок **Управление службами на сервере** в центре администрирования. Кроме того, проверьте консольное приложение «Службы» в разделе «Администрирование».  
  
 Для книг [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] , созданных в [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для Excel версии SQL Server 2008 R2, необходимо установить поставщик OLE DB служб Analysis Services версии SQL Server 2008 R2. Эта ошибка возникает, если поставщик установлен, но файл Microsoft.AnalysisServices.ChannelTransport.dll не зарегистрирован. Дополнительные сведения о регистрации файла см. в статье [Установка поставщика OLE DB служб Analysis Services на серверах SharePoint](http://msdn.microsoft.com/en-us/2c62daf9-1f2d-4508-a497-af62360ee859).  
  
## <a name="see-also"></a>См. также:  
 [Подключение к данным использует проверку подлинности Windows и не удалось делегировать учетные данные пользователя. Следующие соединения не удалось обновить: данные Power Pivot](../../analysis-services/power-pivot-sharepoint/the-data-connection-user-could-not-be-delegated.md)  
  
  
