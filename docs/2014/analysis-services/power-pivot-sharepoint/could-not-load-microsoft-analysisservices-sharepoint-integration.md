---
title: Не удалось загрузить файл или сборку &#39;Microsoft.Data.Services, Version = 3.5.0.0 Culture = neutral, PublicKeyToken = b77a5c561934e089&#39; или одну из ее зависимостей. Система не может найти указанный файл. | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81ed0f44-8782-462d-af8f-0ba5b975df27
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b0330867bb1ffc9d7715d285b6c2c4c5143fb40c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189160"
---
# <a name="could-not-load-file-or-assembly-39microsoftdataservices-version3500-cultureneutral-publickeytokenb77a5c561934e08939-or-one-of-its-dependencies-the-system-cannot-find-the-file-specified"></a>Не удалось загрузить файл или сборку &#39;Microsoft.Data.Services, Version = 3.5.0.0 Culture = neutral, PublicKeyToken = b77a5c561934e089&#39; или одну из ее зависимостей. Система не может найти указанный файл.
  В средах SharePoint 2010 с PowerPivot для SharePoint эта ошибка возникает при попытке выполнить экспорт веб-канала данных, когда в системе отсутствует требуемая версия службы Microsoft ADO.NET Data Services.  
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Область применения|PowerPivot для SharePoint|  
|Номер версии продукта|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Причина|Служба ADO.NET Data Services 3.5 с пакетом обновления 1 (SP1) не найдена.|  
|Текст сообщения|Не удалось загрузить файл или сборку «Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089» или одну из его зависимостей. Система не может найти указанный файл.|  
  
## <a name="explanation"></a>Объяснение  
 В SharePoint 2010 есть кнопка «Экспортировать как веб-канал данных», с помощью которой можно экспортировать список SharePoint в виде веб-канала данных XML. Кроме того, и службы Reporting Services в режиме SharePoint, и PowerPivot для SharePoint поддерживают функции веб-канала данных, для которых требуются службы ADO.NET Data Services.  
  
 Если служба ADO.NET Data Services не установлена, то при запросе веб-канала данных возникнет эта ошибка.  
  
## <a name="user-action"></a>Действие пользователя  
  
1.  Перейдите в документации требования к оборудованию и программному обеспечению для SharePoint 2010, [определить оборудованию и программному обеспечению (SharePoint 2010)](http://go.microsoft.com/fwlink/?LinkId=169734) (http://go.microsoft.com/fwlink/?LinkId=169734).  
  
2.  Найдите в разделе **Установить необходимые программы**ссылку на ADO.NET Data Services 3.5, соответствующую используемой операционной системе.  
  
3.  Щелкните ссылку и запустите программу установки службы.  
  
## <a name="see-also"></a>См. также  
 [Развертывание решений PowerPivot в SharePoint](deploy-power-pivot-solutions-to-sharepoint.md)  
  
  