---
title: "Применение бизнес-правил (надстройка MDS для Excel) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd106345-f561-4966-88d3-a69139b2bd78
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7bcf554389f2e768b4d49741b00bcb829a600aa0
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="apply-business-rules-mds-add-in-for-excel"></a>Применение бизнес-правил (надстройка MDS для Excel)
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] можно применить бизнес-правила, когда необходимо проверить данные и подтвердить их правильность. Затем можно исправить выявленные проблемы и повторно опубликовать данные.  
  
> [!NOTE]  
>  Проверка данных выполняется автоматически при их публикации. Дополнительные сведения см. в разделе [Проверка (службы Master Data Services)](../../master-data-services/validation-master-data-services.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   Необходимо иметь доступ к функциональной области **Обозреватель** .  
  
-   Необходимо иметь активный лист, содержащий данные, управляемые MDS.  
  
### <a name="to-apply-business-rules"></a>Применение бизнес-правил  
  
1.  В группе **Публикация и проверка** нажмите **Применить правила**.  
  
    > [!NOTE]  
    >  Число элементов (строк), проверяемых за один раз, зависит от значения параметра в [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]. Дополнительные сведения см. в статье [Business Rule Settings](../../master-data-services/system-settings-master-data-services.md#BusinessRules).  
  
2.  Данные проверяются по бизнес-правилам, после чего отображаются два столбца состояния. Если эти столбцы не отобразились автоматически, в группе **Публикация и проверка** нажмите кнопку **Показать состояние** , чтобы увидеть их.  
  
## <a name="see-also"></a>См. также:  
 [Обзор импорта данных из Excel (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
