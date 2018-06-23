---
title: 'При попытке установить соединение с внешним источником данных произошла ошибка. Следующие соединения не удалось обновить: данные PowerPivot | Документы Microsoft'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b951da1-f62d-43d2-b40b-270a4a9ab92c
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 36c9846ec1af5589f7fb29d3486ef11632eb01fd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36094877"
---
# <a name="an-error-occurred-during-an-attempt-to-establish-a-connection-to-the-external-data-source-the-following-connections-failed-to-refresh-powerpivot-data"></a>При попытке установить соединение с внешним источником данных произошла ошибка. Следующие соединения не удалось обновить: Данные PowerPivot
  Эта ошибка возникает во время запроса данных PowerPivot на сервере, где не установлен PowerPivot для SharePoint. Она также возникает в случае, если службы SQL Server Analysis Services (PowerPivot) остановлены, или при попытке просмотра данных PowerPivot предыдущей версии.  
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Область применения|PowerPivot для SharePoint|  
|Номер версии продукта|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Причина|Ошибка подключения к данным.|  
|Текст сообщения|При попытке установить соединение с внешним источником данных произошла ошибка. Следующие соединения не удалось обновить: Данные PowerPivot|  
  
## <a name="explanation"></a>Объяснение  
 Службы Excel возвращают эту ошибку во время запроса данных PowerPivot в книге Excel, которая опубликована на сайте SharePoint, при этом в среде SharePoint не установлен сервер PowerPivot для SharePoint, либо служба SQL Server Analysis Services (PowerPivot) остановлена.  
  
 Эта ошибка возникает при срезе или фильтрации данных PowerPivot, когда ядро запросов недоступно.  
  
## <a name="user-action"></a>Действие пользователя  
 Установите PowerPivot для SharePoint или переместите книгу PowerPivot в среду SharePoint, где установлен экземпляр PowerPivot для SharePoint. Дополнительные сведения см. в разделе [PowerPivot for SharePoint 2010 Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md).  
  
 Если установлено программное обеспечение, убедитесь, что экземпляр служб SQL Server Analysis Services (PowerPivot) запущен. Установите флажок **Управление службами на сервере** в центре администрирования. Кроме того, проверьте консольное приложение «Службы» в разделе «Администрирование».  
  
 Для книг PowerPivot, созданных в версии PowerPivot для Excel SQL Server 2008 R2, необходимо установить поставщик OLE DB служб Analysis Services версии SQL Server 2008 R2. Эта ошибка возникает, если поставщик установлен, но файл Microsoft.AnalysisServices.ChannelTransport.dll не зарегистрирован. Дополнительные сведения о регистрации файла см. в статье [Установка поставщика OLE DB служб Analysis Services на серверах SharePoint](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).  
  
## <a name="see-also"></a>См. также  
 [Подключение к данным использует проверку подлинности Windows, а учетные данные невозможно делегировать. Следующие подключения не удалось обновить: данные PowerPivot](the-data-connection-user-could-not-be-delegated.md)  
  
  