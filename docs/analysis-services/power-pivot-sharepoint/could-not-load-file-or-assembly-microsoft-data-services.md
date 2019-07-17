---
title: Не удалось загрузить файл или сборку служб данных Майкрософт | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9472fffb790d8d18ced8d2a528011927717aabc6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68164157"
---
# <a name="could-not-load-file-or-assembly-microsoft-data-services"></a>Не удалось загрузить файл или сборку служб данных Майкрософт
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  В средах SharePoint 2010 с [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint эта ошибка возникает при попытке выполнить экспорт веб-канала данных, когда в системе отсутствует требуемая версия службы Microsoft ADO.NET Data Services.  
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Область применения|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint|  
|Номер версии продукта|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Причина|Служба ADO.NET Data Services 3.5 с пакетом обновления 1 (SP1) не найдена.|  
|Текст сообщения|Не удалось загрузить файл или сборку «Microsoft.Data.Services, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089» или одну из его зависимостей. Система не может найти указанный файл.|  
  
## <a name="explanation"></a>Объяснение  
 В SharePoint 2010 есть кнопка «Экспортировать как веб-канал данных», с помощью которой можно экспортировать список SharePoint в виде веб-канала данных XML. Кроме того, и службы Reporting Services в режиме интеграции с SharePoint, и [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint поддерживают функции веб-канала данных, для которых требуются службы ADO.NET Data Services.  
  
 Если служба ADO.NET Data Services не установлена, то при запросе веб-канала данных возникнет эта ошибка.  
  
## <a name="user-action"></a>Действие пользователя  
  
1.  Перейдите к документации требования к оборудованию и программному обеспечению для SharePoint 2010, [определить оборудованию и программному обеспечению (SharePoint 2010)](http://go.microsoft.com/fwlink/?LinkId=169734) (http://go.microsoft.com/fwlink/?LinkId=169734).  
  
2.  Найдите в разделе **Установить необходимые программы**ссылку на ADO.NET Data Services 3.5, соответствующую используемой операционной системе.  
  
3.  Щелкните ссылку и запустите программу установки службы.  
  
## <a name="see-also"></a>См. также  
 [Развертывание решений PowerPivot в SharePoint](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
