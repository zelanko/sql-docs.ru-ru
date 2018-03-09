---
title: "Поиск отчетов и других элементов (построитель отчетов и службы SSRS) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-builder
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a586659-5c2b-453b-8f40-a3a469277b17
caps.latest.revision: "7"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 163cce974197bba99b31f1de97f8868653ffa015
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="searching-for-reports-and-other-items-report-builder--and-ssrs"></a>Поиск отчетов и других элементов (построитель отчетов и службы SSRS)
  Можно использовать диспетчер отчетов для поиска на сервере отчетов заданных элементов по имени или описанию. Можно искать опубликованные отчеты, модели отчетов, папки, общие источники данных и ресурсы. Нельзя искать расписания, владельцев, назначения ролей, определенные моментальные снимки в журнале отчета или в подписках. Поиск выполняется в базе данных сервера отчетов, в которой хранятся элементы.  
  
> [!NOTE]  
>  Выполнение поиска системного файла не вернет результаты поиска для элементов, управляемых сервером отчетов.  
  
-   Чтобы начать поиск элементов в диспетчере отчетов, введите строку поиска в текстовом поле **Поиск** вверху страницы. Поиски начинаются с высшего узла иерархии папок и затем следуют через каждую ветку. Если отсутствует разрешение на доступ к определенной ветке, то эта ветка пропускается. Это относится к папкам «Мои отчеты», принадлежащим другим пользователям и другим папкам, которые обычно не доступны. Только отчеты и элементы, на которые есть разрешение просмотра, включаются в результаты поиска.  
  
-   Чтобы найти элемент по имени или описанию, укажите весь текст или часть текста, с которым нужно совпадение. В строке поиска регистр букв не учитывается. Нельзя использовать операторы поиска, такие как символы плюс (+) или минус (-), для требования или исключения критерия поиска.  
  
-   Для поиска определенного текста в отчете используется панель инструментов, расположенная в верхней части отчета.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Поиск и просмотр отчетов в диспетчере отчетов (построитель отчетов и службы SSRS)](finding-and-viewing-reports-with-a-browser-report-builder-and-ssrs.md)   
 [Использование папки "Мои отчеты" (построитель отчетов и службы SSRS)](../../reporting-services/report-builder/using-my-reports-report-builder-and-ssrs.md)   
 [Поиск, просмотр отчетов и управление ими (построитель отчетов и службы SSRS)](../../reporting-services/report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)   
 [Открытие и закрытие отчетов (диспетчер отчетов)](../../reporting-services/reports/open-and-close-a-report-report-manager.md)  
  
  
