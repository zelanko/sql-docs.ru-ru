---
title: Импорт данных из Excel в службы Master Data Services (надстройка MDS для Excel) | Документы Майкрософт
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 89fce454-a816-4b33-a26a-d1b9741d269b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 093f8a471210b73b8c3cdaf1b2bb083b31980c52
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68092282"
---
# <a name="import-data-from-excel-to-master-data-services-mds-add-in-for-excel"></a>Импорт данных из Excel в службы Master Data Services (надстройка MDS для Excel)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]необходимо по окончании работы в Excel выполнить публикацию данных в репозитории MDS, чтобы другие пользователи могли получить к ним доступ.  
  
> [!NOTE]
>  -   Комментарии в ячейках, управляемых MDS, при публикации изменений удаляются.  
> -   Формула не поддерживается в ячейке, управляемой MDS. Формула в управляемой MDS ячейке обрабатывается как текстовое значение.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
-   Активный лист должен содержать данные, управляемые MDS, и в эти данные должны быть внесены изменения или дополнения.  
  
-   Если добавляются новые элементы, то для них не нужно указывать значение **Code** , если формирование кодов сущностей производится автоматически. Дополнительные сведения см. в разделе [Автоматическое создание кодов (службы Master Data Services)](../../master-data-services/automatic-code-creation-master-data-services.md).  
  
### <a name="to-publish-data-to-the-mds-repository"></a>Публикация данных в репозитории MDS  
  
1.  В группе **Публикация и проверка** нажмите **Опубликовать**.  
  
2.  Необязательный параметр. Если открылось диалоговое окно **Публикация и заметки** , то выберите либо использование одной заметки (комментария) для всех обновлений, либо задание заметок отдельно для каждого изменения.  
  
3.  Необязательный параметр. Выберите флажок **Больше не показывать это диалоговое окно** . Его отображение можно будет в любой момент включить, выбрав **Настройки** и установив флажок **Показывать диалоговое окно «Публикация и заметки» при публикации** .  
  
4.  Нажмите кнопку **Опубликовать**.  
  
> [!NOTE]  
>  Если при добавлении на лист новых элементов (строк) их не удалось успешно опубликовать в репозитории MDS, то, возможно, у вас нет разрешения **Обновление** для всех атрибутов листа. На вкладке **Просмотр** в группе **Изменения** нажмите **Снять защиту листа** и повторите попытку публикации.  
  
## <a name="next-steps"></a>Следующие шаги  
 [Применение бизнес-правил (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/apply-business-rules-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>См. также  
 [Обзор: импорт данных из Excel &#40;надстройка MDS для Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)   
 [Проверка данных (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/validating-data-mds-add-in-for-excel.md)  
  
  
