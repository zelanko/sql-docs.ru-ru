---
title: "Устранение неполадок с диаграммами (построитель отчетов и службы SSRS) | Документы Майкрософт"
ms.custom: 
ms.date: 01/17/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: report-design
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a327ffa-3b69-40d6-8015-cc01cfae9161
caps.latest.revision: 
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3d9c4af51de2ac435bbdcefe1d66e0d0a59326e5
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/19/2018
---
# <a name="troubleshoot-charts-report-builder-and-ssrs"></a>Устранение неполадок с диаграммами (построитель отчетов и службы SSRS)
  При работе с диаграммами могут возникать следующие вопросы.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="why-does-my-chart-count-not-sum-the-values-on-the-value-axis"></a>Почему в диаграмме выполняется подсчет, а не суммирование значений по оси значений?  
 Для верного отображения многих типов диаграмм требуются числовые значения по оси значений (обычно это ось Y). Если поле значения имеет тип **String**, диаграмме не удастся отобразить числовые значения, даже если поля содержат числа. Вместо этого диаграмма отображает общее число строк, содержащих значение в этом поле. Чтобы избежать подобного поведения, убедитесь, что поля, используемые для рядов значений, имеют числовые типы данных, а не являются строками, содержащими числа.  

## <a name="need-more-help"></a>Требуется дополнительная помощь?  
   
  Попробуйте:  
 * [SQL Server Reporting Services](https://stackoverflow.com/questions/tagged/reporting-services) на Stack Overflow  
 * Опубликуйте информацию о проблеме или предложение на [Microsoft SQL Server UserVoice](https://feedback.azure.com/forums/908035-sql-server).  
  
## <a name="see-also"></a>См. также:  
 [Диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
