---
title: "Не удалось загрузить «Microsoft.AnalysisServices.SharePoint.Integration» | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6e350b67-5e18-4b90-8fb7-a0109cbb27b7
caps.latest.revision: "7"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0854f5c3cdf740c68b8f83dcb3d847cefc256edd
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="could-not-load-microsoftanalysisservicessharepointintegration"></a>Не удалось загрузить Microsoft.AnalysisServices.SharePoint.Integration
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]В средах SharePoint 2010 с [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint, эта ошибка возникает, если решение уровня приложения для [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] развернуто неправильно.  
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Область применения|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint|  
|Номер версии продукта|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Причина|Решение Powerpivotwebapp не развернуто или развернуто неправильно.|  
|Текст сообщения|Не удалось загрузить файл или сборку Microsoft.AnalysisServices.SharePoint.Integration|  
  
## <a name="explanation"></a>Объяснение  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint использует пакеты решений для развертывания своих компонентов на сервере SharePoint. Одно из решений развернуто неправильно. Поэтому при попытке открыть коллекцию [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] или другие страницы приложения [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] на сайте SharePoint возникает эта ошибка.  
  
## <a name="user-action"></a>Действие пользователя  
 Выполните развертывание пакета решения.  
  
1.  В разделе «Системные параметры» центра администрирования выберите **Управление решениями фермы**.  
  
2.  Щелкните **Powerpivotwebapp**.  
  
3.  Нажмите **Развернуть решение**.  
  
4.  Выберите веб-приложение, для которого возникает эта ошибка. Если имеются несколько веб-приложений, выполните повторное развертывание для них всех.  
  
5.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  
 [Развертывание решений PowerPivot в SharePoint](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
