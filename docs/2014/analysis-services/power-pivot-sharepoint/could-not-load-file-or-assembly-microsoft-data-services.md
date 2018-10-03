---
title: Не удалось загрузить файл или сборку &#39;Microsoft.AnalysisServices.SharePoint.Integration&#39; | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 6e350b67-5e18-4b90-8fb7-a0109cbb27b7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2b8328c060d7096cb43edcbc31206a8b55e82e7e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48049214"
---
# <a name="could-not-load-file-or-assembly-39microsoftanalysisservicessharepointintegration39"></a>Не удалось загрузить файл или сборку &#39;Microsoft.AnalysisServices.SharePoint.Integration&#39;
  В среде SharePoint 2010, в которой установлен PowerPivot для SharePoint, эта ошибка возникает, если решение на уровне приложений для PowerPivot развернуто неправильно.  
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Область применения|PowerPivot для SharePoint|  
|Номер версии продукта|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Причина|Решение Powerpivotwebapp не развернуто или развернуто неправильно.|  
|Текст сообщения|Не удалось загрузить файл или сборку Microsoft.AnalysisServices.SharePoint.Integration|  
  
## <a name="explanation"></a>Объяснение  
 PowerPivot для SharePoint использует пакеты решений для развертывания своих компонентов на сервере SharePoint. Одно из решений развернуто неправильно. Поэтому при попытке открыть галерею PowerPivot или другие страницы приложения PowerPivot на сайте SharePoint возникает эта ошибка.  
  
## <a name="user-action"></a>Действие пользователя  
 Выполните развертывание пакета решения.  
  
1.  В разделе «Системные параметры» центра администрирования выберите **Управление решениями фермы**.  
  
2.  Щелкните **Powerpivotwebapp**.  
  
3.  Нажмите **Развернуть решение**.  
  
4.  Выберите веб-приложение, для которого возникает эта ошибка. Если имеются несколько веб-приложений, выполните повторное развертывание для них всех.  
  
5.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Развертывание решений PowerPivot в SharePoint](deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
