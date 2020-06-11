---
title: 'При попытке установить соединение с внешним источником данных произошла ошибка. Не удалось обновить следующие соединения: данные PowerPivot | Документация Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1b951da1-f62d-43d2-b40b-270a4a9ab92c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 242fefb2ca22d7b0129268a8a3ea8ed98e80bbe3
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547616"
---
# <a name="an-error-occurred-during-an-attempt-to-establish-a-connection-to-the-external-data-source-the-following-connections-failed-to-refresh-powerpivot-data"></a>При попытке установить соединение с внешним источником данных произошла ошибка. Следующие соединения не удалось обновить: данные PowerPivot
  Эта ошибка возникает во время запроса данных PowerPivot на сервере, где не установлен PowerPivot для SharePoint. Она также возникает в случае, если службы SQL Server Analysis Services (PowerPivot) остановлены, или при попытке просмотра данных PowerPivot предыдущей версии.  
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Применяется к|PowerPivot для SharePoint|  
|Версия продукта|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Причина|Ошибка подключения к данным.|  
|Текст сообщения|При попытке установить соединение с внешним источником данных произошла ошибка. Следующие соединения не удалось обновить: данные PowerPivot|  
  
## <a name="explanation"></a>Объяснение  
 Службы Excel возвращают эту ошибку во время запроса данных PowerPivot в книге Excel, которая опубликована на сайте SharePoint, при этом в среде SharePoint не установлен сервер PowerPivot для SharePoint, либо служба SQL Server Analysis Services (PowerPivot) остановлена.  
  
 Эта ошибка возникает при срезе или фильтрации данных PowerPivot, когда ядро запросов недоступно.  
  
## <a name="user-action"></a>Действие пользователя  
 Установите PowerPivot для SharePoint или переместите книгу PowerPivot в среду SharePoint, где установлен экземпляр PowerPivot для SharePoint. Дополнительные сведения см. в разделе [PowerPivot for SharePoint 2010 Installation](../../sql-server/install/powerpivot-for-sharepoint-2010-installation.md).  
  
 Если установлено программное обеспечение, убедитесь, что экземпляр служб SQL Server Analysis Services (PowerPivot) запущен. Установите флажок **Управление службами на сервере** в центре администрирования. Кроме того, проверьте консольное приложение «Службы» в разделе «Администрирование».  
  
 Для книг PowerPivot, созданных в версии PowerPivot для Excel SQL Server 2008 R2, необходимо установить поставщик OLE DB служб Analysis Services версии SQL Server 2008 R2. Эта ошибка возникает, если поставщик установлен, но файл Microsoft.AnalysisServices.ChannelTransport.dll не зарегистрирован. Дополнительные сведения о регистрации файла см. в статье [Установка поставщика OLE DB служб Analysis Services на серверах SharePoint](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).  
  
## <a name="see-also"></a>См. также:  
 [При подключении к данным используется проверка подлинности Windows, а учетные данные пользователя не могут быть делегированы. Не удалось обновить следующие соединения: данные PowerPivot](the-data-connection-user-could-not-be-delegated.md)  
  
  
