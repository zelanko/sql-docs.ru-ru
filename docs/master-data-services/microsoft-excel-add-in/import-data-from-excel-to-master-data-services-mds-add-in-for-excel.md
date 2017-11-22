---
title: "Импорт данных из Excel в службы Master Data Services (надстройка MDS для Excel) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: mds
ms.service: 
ms.component: microsoft-excel-add-in
ms.reviewer: 
ms.suite: sql
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89fce454-a816-4b33-a26a-d1b9741d269b
caps.latest.revision: "10"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5bc2811d9afc590d7f801c5529b80914e16ef043
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="import-data-from-excel-to-master-data-services-mds-add-in-for-excel"></a>Импорт данных из Excel в службы Master Data Services (надстройка MDS для Excel)
  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]необходимо по окончании работы в Excel выполнить публикацию данных в репозитории MDS, чтобы другие пользователи могли получить к ним доступ.  
  
> [!NOTE]  
>  -   Комментарии в ячейках, управляемых MDS, при публикации изменений удаляются.  
> -   Формула не поддерживается в ячейке, управляемой MDS. Формула в управляемой MDS ячейке обрабатывается как текстовое значение.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
-   Активный лист должен содержать данные, управляемые MDS, и в эти данные должны быть внесены изменения или дополнения.  
  
-   Если добавляются новые элементы, то для них не нужно указывать значение **Code** , если формирование кодов сущностей производится автоматически. Дополнительные сведения см. в разделе [Автоматическое создание кодов (службы Master Data Services)](../../master-data-services/automatic-code-creation-master-data-services.md).  
  
### <a name="to-publish-data-to-the-mds-repository"></a>Публикация данных в репозитории MDS  
  
1.  В группе **Публикация и проверка** нажмите **Опубликовать**.  
  
2.  Необязательно. Если открылось диалоговое окно **Публикация и заметки** , то выберите либо использование одной заметки (комментария) для всех обновлений, либо задание заметок отдельно для каждого изменения.  
  
3.  Необязательно. Выберите флажок **Больше не показывать это диалоговое окно** . Его отображение можно будет в любой момент включить, выбрав **Настройки** и установив флажок **Показывать диалоговое окно «Публикация и заметки» при публикации** .  
  
4.  Нажмите кнопку **Опубликовать**.  
  
> [!NOTE]  
>  Если при добавлении на лист новых элементов (строк) их не удалось успешно опубликовать в репозитории MDS, то, возможно, у вас нет разрешения **Обновление** для всех атрибутов листа. На вкладке **Просмотр** в группе **Изменения** нажмите **Снять защиту листа** и повторите попытку публикации.  
  
## <a name="next-steps"></a>Следующие шаги  
 [Применение бизнес-правил (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/apply-business-rules-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>См. также:  
 [Обзор импорта данных из Excel (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)   
 [Проверка данных (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/validating-data-mds-add-in-for-excel.md)  
  
  
