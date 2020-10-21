---
description: Импорт данных из Excel в службы Master Data Services (надстройка MDS для Excel)
title: Импорт данных из Excel
ms.custom: microsoft-excel-add-in, seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 89fce454-a816-4b33-a26a-d1b9741d269b
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a06d8338f334074ede68f34c8145f0d8fecb529f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "92257751"
---
# <a name="import-data-from-excel-to-master-data-services-mds-add-in-for-excel"></a>Импорт данных из Excel в службы Master Data Services (надстройка MDS для Excel)

[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  В [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]необходимо по окончании работы в Excel выполнить публикацию данных в репозитории MDS, чтобы другие пользователи могли получить к ним доступ.  
  
> [!NOTE]
>  -   Комментарии в ячейках, управляемых MDS, при публикации изменений удаляются.  
> -   Формула не поддерживается в ячейке, управляемой MDS. Формула в управляемой MDS ячейке обрабатывается как текстовое значение.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
-   Активный лист должен содержать данные, управляемые MDS, и в эти данные должны быть внесены изменения или дополнения.  
  
-   Если добавляются новые элементы, то для них не нужно указывать значение **Code** , если формирование кодов сущностей производится автоматически. Дополнительные сведения см. в разделе [Автоматическое создание кода &#40;Master Data Services&#41;](../../master-data-services/automatic-code-creation-master-data-services.md).  
  
### <a name="to-publish-data-to-the-mds-repository"></a>Публикация данных в репозитории MDS  
  
1.  В группе **Публикация и проверка** нажмите **Опубликовать**.  
  
2.  Необязательный элемент. Если открылось диалоговое окно **Публикация и заметки** , то выберите либо использование одной заметки (комментария) для всех обновлений, либо задание заметок отдельно для каждого изменения.  
  
3.  Необязательный элемент. Выберите флажок **Больше не показывать это диалоговое окно** . Его отображение можно будет в любой момент включить, выбрав **Настройки** и установив флажок **Показывать диалоговое окно «Публикация и заметки» при публикации** .  
  
4.  Нажмите кнопку **Опубликовать**.  
  
> [!NOTE]  
>  Если при добавлении на лист новых элементов (строк) их не удалось успешно опубликовать в репозитории MDS, то, возможно, у вас нет разрешения **Обновление** для всех атрибутов листа. На вкладке **Просмотр** в группе **Изменения** нажмите **Снять защиту листа** и повторите попытку публикации.  
  
## <a name="next-steps"></a>Next Steps  
 [Применение бизнес-правил (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/apply-business-rules-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>См. также:  
 [Обзор. Импорт данных из надстройка MDS для Excel &#40;Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)   
 [Проверка данных (надстройка MDS для Excel)](../../master-data-services/microsoft-excel-add-in/validating-data-mds-add-in-for-excel.md)  
  
  
