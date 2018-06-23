---
title: Применение бизнес-правил (надстройка MDS для Excel) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cd106345-f561-4966-88d3-a69139b2bd78
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: be74d232575f396ae491a3475d632f58fb55a1ce
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191219"
---
# <a name="apply-business-rules-mds-add-in-for-excel"></a>Применение бизнес-правил (надстройка MDS для Excel)
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] можно применить бизнес-правила, когда необходимо проверить данные и подтвердить их правильность. Затем можно исправить выявленные проблемы и повторно опубликовать данные.  
  
> [!NOTE]  
>  Проверка данных выполняется автоматически при их публикации. Дополнительные сведения см. в разделе [Проверка хранимых процедур (службы Master Data Services)](../validation-stored-procedure-master-data-services.md).  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь доступ к функциональной области **Обозреватель** .  
  
-   Необходимо иметь активный лист, содержащий данные, управляемые MDS.  
  
### <a name="to-apply-business-rules"></a>Применение бизнес-правил  
  
1.  В группе **Публикация и проверка** нажмите **Применить правила**.  
  
    > [!NOTE]  
    >  Число элементов (строк), проверяемых за один раз, зависит от значения параметра в [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]. Дополнительные сведения см. в статье [Business Rule Settings](../system-settings-master-data-services.md#BusinessRules).  
  
2.  Данные проверяются по бизнес-правилам, после чего отображаются два столбца состояния. Если эти столбцы не отобразились автоматически, в группе **Публикация и проверка** нажмите кнопку **Показать состояние** , чтобы увидеть их.  
  
## <a name="see-also"></a>См. также  
 [Публикация данных &#40;надстройка MDS для Excel&#41;](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  