---
title: Применение бизнес-правил (надстройка MDS для Excel) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cd106345-f561-4966-88d3-a69139b2bd78
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 32819a694769092c255c4b2ed918dd8fde99362e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "65482606"
---
# <a name="apply-business-rules-mds-add-in-for-excel"></a>Применение бизнес-правил (надстройка MDS для Excel)
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] можно применить бизнес-правила, когда необходимо проверить данные и подтвердить их правильность. Затем можно исправить выявленные проблемы и повторно опубликовать данные.  
  
> [!NOTE]  
>  Проверка данных выполняется автоматически при их публикации. Дополнительные сведения см. в разделе [Проверка хранимых процедур (службы Master Data Services)](../validation-stored-procedure-master-data-services.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь доступ к функциональной области **Обозреватель** .  
  
-   Необходимо иметь активный лист, содержащий данные, управляемые MDS.  
  
### <a name="to-apply-business-rules"></a>Применение бизнес-правил  
  
1.  В группе **Публикация и проверка** нажмите **Применить правила**.  
  
    > [!NOTE]  
    >  Число элементов (строк), проверяемых за один раз, зависит от значения параметра в [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]. Дополнительные сведения см. в статье [Business Rule Settings](../system-settings-master-data-services.md#BusinessRules).  
  
2.  Данные проверяются по бизнес-правилам, после чего отображаются два столбца состояния. Если эти столбцы не отобразились автоматически, в группе **Публикация и проверка** нажмите кнопку **Показать состояние** , чтобы увидеть их.  
  
## <a name="see-also"></a>См. также:  
 [Публикация &#40;данных надстройка MDS для Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
