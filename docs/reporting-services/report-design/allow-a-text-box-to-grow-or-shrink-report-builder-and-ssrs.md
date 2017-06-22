---
title: "Разрешение для текстового поля для увеличения или сжатия (построитель отчетов и службы SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dbc01e78-5993-47e5-af04-34f9e3bbcee1
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: abb928e42a7420b421c91f6b5f78256213cb5df9
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="allow-a-text-box-to-grow-or-shrink-report-builder-and-ssrs"></a>Разрешение расширения или сжатия для текстового поля (построитель отчетов и службы SSRS)
  В отчете [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] с разбиением на страницы текстовые поля являются не просто изолированными полями в области конструктора отчета. Каждая ячейка в таблице или матрице (области данных табликса) содержит текстовое поле, которое можно форматировать аналогично изолированным текстовым полям в отчете. По умолчанию текстовые поля имеют фиксированный размер. Можно задать параметры, позволяющие текстовому полю расширяться или сжиматься в соответствии с содержимым. Эти параметры соответствуют свойствам **CanGrow** и **CanShrink** на панели свойств.  
  
## <a name="to-allow-a-text-box-to-grow-or-shrink"></a>Расширение или сжатие для текстового поля  
  
1.  Щелкните правой кнопкой мыши текстовое поле и выберите пункт **Свойства текстового поля**.  
  
2.  Перейдите на вкладку **Общие** .  
  
    -   Чтобы включить расширение текстового поля по вертикали в соответствии с содержимым, установите флажок **Разрешить увеличение высоты**.  
  
    -   Чтобы включить сжатие текстового поля в соответствии с содержимым, установите флажок **Разрешить уменьшение высоты**.  
  
## <a name="see-also"></a>См. также  
 [Текстовые поля (построитель отчетов и службы SSRS)](../../reporting-services/report-design/text-boxes-report-builder-and-ssrs.md)  
  
  
