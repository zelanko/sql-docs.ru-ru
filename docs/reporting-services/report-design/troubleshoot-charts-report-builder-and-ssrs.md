---
title: "Устранение неполадок с диаграммами (построитель отчетов и службы SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a327ffa-3b69-40d6-8015-cc01cfae9161
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 7
---
# Устранение неполадок с диаграммами (построитель отчетов и службы SSRS)
  При работе с диаграммами могут возникать следующие вопросы.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Почему в диаграмме выполняется подсчет, а не суммирование значений по оси значений?  
 Для верного отображения многих типов диаграмм требуются числовые значения по оси значений (обычно это ось Y). Если поле значения имеет тип **String**, диаграмме не удастся отобразить числовые значения, даже если поля содержат числа. Вместо этого диаграмма отображает общее число строк, содержащих значение в этом поле. Чтобы избежать подобного поведения, убедитесь, что поля, используемые для рядов значений, имеют числовые типы данных, а не являются строками, содержащими числа.  
  
## См. также  
 [Диаграммы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  