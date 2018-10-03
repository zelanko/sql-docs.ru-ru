---
title: Устранение неполадок с диаграммами (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.date: 01/17/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 3a327ffa-3b69-40d6-8015-cc01cfae9161
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 65dac70a2b3eebc090cf282d650aff3840d00e89
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47738674"
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
  
  
