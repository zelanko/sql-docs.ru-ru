---
title: Не удалось загрузить файл или сборку &#39;Microsoft. Data. Services, Version = 3.5.0.0, культура = Neutral, PublicKeyToken = b77a5c561934e089»&#39; или одну из его зависимостей. Системе не удается найти указанный файл. | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 81ed0f44-8782-462d-af8f-0ba5b975df27
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9bcfdde8b3536bbbf8b2429d51a9ee9aecf0d437
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547506"
---
# <a name="could-not-load-file-or-assembly-39microsoftdataservices-version3500-cultureneutral-publickeytokenb77a5c561934e08939-or-one-of-its-dependencies-the-system-cannot-find-the-file-specified"></a>Не удалось загрузить файл или сборку &#39;Microsoft. Data. Services, Version = 3.5.0.0, культура = Neutral, PublicKeyToken = b77a5c561934e089»&#39; или одну из его зависимостей. Системе не удается найти указанный файл.
  В средах SharePoint 2010 с PowerPivot для SharePoint эта ошибка возникает при попытке выполнить экспорт веб-канала данных, когда в системе отсутствует требуемая версия службы Microsoft ADO.NET Data Services.  
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Применяется к|PowerPivot для SharePoint|  
|Версия продукта|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Причина|Служба ADO.NET Data Services 3.5 с пакетом обновления 1 (SP1) не найдена.|  
|Текст сообщения|Не удалось загрузить файл или сборку «Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089» или одну из его зависимостей. Система не может найти указанный файл.|  
  
## <a name="explanation"></a>Объяснение  
 В SharePoint 2010 есть кнопка «Экспортировать как веб-канал данных», с помощью которой можно экспортировать список SharePoint в виде веб-канала данных XML. Кроме того, и службы Reporting Services в режиме SharePoint, и PowerPivot для SharePoint поддерживают функции веб-канала данных, для которых требуются службы ADO.NET Data Services.  
  
 Если служба ADO.NET Data Services не установлена, то при запросе веб-канала данных возникнет эта ошибка.  
  
## <a name="user-action"></a>Действие пользователя  
  
1.  Перейдите к документации по требованиям к оборудованию и программному обеспечению для SharePoint 2010, [Определите требования к оборудованию и программному обеспечению (SharePoint 2010)](https://go.microsoft.com/fwlink/?LinkId=169734) ( https://go.microsoft.com/fwlink/?LinkId=169734) .  
  
2.  Найдите в разделе **Установить необходимые программы**ссылку на ADO.NET Data Services 3.5, соответствующую используемой операционной системе.  
  
3.  Щелкните ссылку и запустите программу установки службы.  
  
## <a name="see-also"></a>См. также:  
 [Развертывание решений PowerPivot в SharePoint](deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
