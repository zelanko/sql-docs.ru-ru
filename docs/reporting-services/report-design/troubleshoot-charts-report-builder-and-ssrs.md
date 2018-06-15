---
title: Устранение неполадок с диаграммами (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 01/17/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-design
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3a327ffa-3b69-40d6-8015-cc01cfae9161
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e9bd6c14bcc6157b65d851d25019c8090a8f8485
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "33024251"
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
  
  
