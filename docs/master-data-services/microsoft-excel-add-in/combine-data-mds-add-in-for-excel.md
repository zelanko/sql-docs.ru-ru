---
title: Объединение данных (надстройка MDS для Excel) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.service: ''
ms.component: microsoft-excel-add-in
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a867dc15-5a0d-457c-8304-ac323bcf9377
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 151b16f039c59eef84360ddfb7682ab97d437160
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="combine-data-mds-add-in-for-excel"></a>Объединение данных (надстройка MDS для Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]объедините данные из двух листов, чтобы сравнить их перед публикацией. В этой процедуре данные из двух таблиц объединяются в одну. Затем можно выполнить сравнения и определить, какие данные (если имеются) следует опубликовать в репозитории MDS.  
  
## <a name="prerequisites"></a>предварительные требования  
  
-   Необходимо иметь лист, содержащий данные, управляемые MDS. Дополнительные сведения см. в разделе [Экспорт данных в Excel из служб Master Data Services](../../master-data-services/microsoft-excel-add-in/export-data-to-excel-from-master-data-services.md).  
  
-   Необходимо иметь лист, содержащий данные, которые нужно объединить с данными, управляемыми MDS. Этот лист должен иметь строку заголовка.  
  
### <a name="to-combine-non-managed-data-into-an-mds-managed-sheet"></a>Объединение неуправляемых данных на листе, управляемом MDS  
  
1.  На листе, содержащем данные, управляемые MDS, в группе **Публикация и проверка** нажмите кнопку **Объединить данные**.  
  
2.  В диалоговом окне **Объединение данных** рядом с текстовым полем **Диапазон для объединения с данными MDS** щелкните значок. Диалоговое окно свернется.  
  
3.  Щелкните лист, содержащий данные, которые нужно объединить.  
  
4.  Выделите все ячейки на листе, которые нужно объединить, включая строку заголовка.  
  
5.  В диалоговом окне **Объединение данных** щелкните значок. Диалоговое окно раскроется.  
  
6.  Для столбца, указанного для сущности MDS, выберите столбец в поле **Соответствующий столбец**. Соответствующие столбцы нужны не для всех столбцов MDS.  
  
7.  Нажмите кнопку **Объединить**. Появится столбец **SOURCE** , указывающий, берутся ли данные из MDS или внешнего источника.  
  
## <a name="next-steps"></a>Next Steps  
  
-   Сведения об определении подобия между данными, управляемыми MDS, и внешними данными см. в разделе [Сопоставление схожих данных (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/match-similar-data-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>См. также:  
 [Обзор экспорта данных в Excel (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [Сопоставление качества данных в надстройке MDS для Excel](../../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md)  
  
  
