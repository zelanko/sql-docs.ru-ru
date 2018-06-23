---
title: Устранение неполадок с диаграммами (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a327ffa-3b69-40d6-8015-cc01cfae9161
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: b5369ef0fd3f96345e0fc7e0c688f1230bfe41c1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180204"
---
# <a name="troubleshoot-charts-report-builder-and-ssrs"></a>Устранение неполадок с диаграммами (построитель отчетов и службы SSRS)
  При работе с диаграммами могут возникать следующие вопросы.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="why-does-my-chart-count-not-sum-the-values-on-the-value-axis"></a>Почему в диаграмме выполняется подсчет, а не суммирование значений по оси значений?  
 Для верного отображения многих типов диаграмм требуются числовые значения по оси значений (обычно это ось Y). Если тип данных поле значения `String`, в диаграмме нельзя отобразить числовое значение, даже если поля содержат числа. Вместо этого диаграмма отображает общее число строк, содержащих значение в этом поле. Чтобы избежать подобного поведения, убедитесь, что поля, используемые для рядов значений, имеют числовые типы данных, а не являются строками, содержащими числа.  
  
## <a name="see-also"></a>См. также  
 [Диаграммы &#40;отчетов построителя отчетов и службы SSRS&#41;](charts-report-builder-and-ssrs.md)  
  
  