---
title: Разрешение расширения или сжатия для текстового поля (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: dbc01e78-5993-47e5-af04-34f9e3bbcee1
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f193020ccb75997c5a2ac494906a74c1f27f8b32
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2019
ms.locfileid: "56291942"
---
# <a name="allow-a-text-box-to-grow-or-shrink-report-builder-and-ssrs"></a>Разрешение расширения или сжатия для текстового поля (построитель отчетов и службы SSRS)
  В отчете [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] с разбиением на страницы текстовые поля являются не просто изолированными полями в области конструктора отчета. Каждая ячейка в таблице или матрице (области данных табликса) содержит текстовое поле, которое можно форматировать аналогично изолированным текстовым полям в отчете. По умолчанию текстовые поля имеют фиксированный размер. Можно задать параметры, позволяющие текстовому полю расширяться или сжиматься в соответствии с содержимым. Эти параметры соответствуют свойствам **CanGrow** и **CanShrink** на панели свойств.  
  
## <a name="to-allow-a-text-box-to-grow-or-shrink"></a>Расширение или сжатие для текстового поля  
  
1.  Щелкните правой кнопкой мыши текстовое поле и выберите пункт **Свойства текстового поля**.  
  
2.  Перейдите на вкладку **Общие** .  
  
    -   Чтобы включить расширение текстового поля по вертикали в соответствии с содержимым, установите флажок **Разрешить увеличение высоты**.  
  
    -   Чтобы включить сжатие текстового поля в соответствии с содержимым, установите флажок **Разрешить уменьшение высоты**.  
  
## <a name="see-also"></a>См. также:  
 [Текстовые поля (построитель отчетов и службы SSRS)](../../reporting-services/report-design/text-boxes-report-builder-and-ssrs.md)  
  
  
