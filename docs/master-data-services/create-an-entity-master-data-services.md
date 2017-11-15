---
title: "Создание сущности (службы Master Data Services) | Документы Майкрософт"
ms.custom: SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- entities [Master Data Services], creating
- creating entities [Master Data Services]
ms.assetid: d9a6a51e-7b53-4785-a118-3baeb7ca2d48
caps.latest.revision: "9"
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ef44a2211a8b9d82f1a155542176b45b335d706d
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="create-an-entity-master-data-services"></a>Создание сущности (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]сущности создаются, чтобы содержать элементы и их атрибуты.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Модель должна существовать. Дополнительные сведения см. в разделе [Создание модели (службы Master Data Services)](../master-data-services/create-a-model-master-data-services.md).  
  
### <a name="to-create-an-entity"></a>Создание сущности  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Manage Model** (Управление моделями) в сетке выберите модель, для которой необходимо создать сущность, а затем щелкните **Сущности**.  
  
3.  На странице **Manage Entity** (Управление сущностями) щелкните **Добавить**.  
  
4.  В поле **Имя** введите имя сущности.  
  
5.  При необходимости в поле **Описание** введите описание сущности.  
  
6.  При необходимости в поле **Имя для промежуточных таблиц** введите имя промежуточной таблицы.  
  
     Если это поле оставлено пустым, используется имя сущности.  
  
    > [!TIP]  
    >  Используйте имя модели как часть имени промежуточной таблицы, например *Modelname_Entityname*. Это облегчит поиск таблиц в базе данных. Дополнительные сведения о промежуточных таблицах см. в разделе [Обзор: импорт данных из таблиц (службы Master Data Services)](../master-data-services/overview-importing-data-from-tables-master-data-services.md).  
  
7.  В поле **Тип журнала транзакций** в раскрывающемся списке выберите тип журнала транзакций.  
  
     Дополнительные сведения см. в разделе [Изменение типа журнала транзакций сущности (Master Data Services)](../master-data-services/change-the-entity-transaction-log-type-master-data-services.md)  
  
8.  Необязательно. Установите флажок в поле **Автоматически создавать значения кода** . Дополнительные сведения см. в разделе [Автоматическое создание кодов (службы Master Data Services)](../master-data-services/automatic-code-creation-master-data-services.md).  
  
9. Необязательно. Установите флажок **Включить сжатие данных** . Сжатие строк включено по умолчанию. Дополнительные сведения см. в статье [Data Compression](../relational-databases/data-compression/data-compression.md).  
  
10. Нажмите кнопку **Сохранить**.  
  
## <a name="grid-columns"></a>Столбцы сетки  
 Для каждой созданной сущности в сетке создается строка с тринадцатью столбцами. Ниже приведены эти столбцы.  
  
|Имя|Описание|  
|----------|-----------------|  
|Состояние|Состояние сущности. После нажатия кнопки **Сохранить** появится следующее изображение, которое указывает на то, что сущность обновляется.<br /><br /> ![Значок обновления состояния](../master-data-services/media/mds-statusicon-updating.png "Значок обновления состояния")<br /><br /> При наличии ошибок во время создания или изменения сущности появляется следующее изображение.<br /><br /> ![Значок состояния ошибки](../master-data-services/media/mds-statusicon-error.png "Значок состояния ошибки")<br /><br /> Если ее состояние нормальное, появится следующее изображение.<br /><br /> ![Значок нормального состояния](../master-data-services/media/mds-statusicon-ok.png "Значок нормального состояния")|  
|Имя|Имя сущности.|  
|Описание|Описание сущности.|  
|Промежуточная таблица|Имя префикса таблицы, которая используется для хранения данных.|  
|Тип журнала транзакций|Тип журнала транзакций сущности.|  
|Автоматическое создание кодов|Указывает, включено ли автоматическое создание кода.|  
|Data Compression|Указывает, включено ли сжатие данных для сущности.|  
|Целевой объект синхронизации|Указывает, является ли сущность целевым объектом отношения синхронизации.|  
|Иерархия|Указывает, включено ли для сущности использование явных иерархий. Если для сущности создана хотя бы одна явная иерархия, в столбце отображается значение "Да".|  
|Автор|Имя пользователя, создавшего сущность.|  
|Создана|Дата и время создания сущности.|  
|Кем обновлена|Имя пользователя, выполнившего последнее обновление сущности.|  
|Обновлена|Дата и время последнего обновления сущности.|  
  
## <a name="next-steps"></a>Следующие шаги  
  
-   [Создание текстового атрибута (службы Master Data Services)](../master-data-services/create-a-text-attribute-master-data-services.md)  
  
-   [Создание атрибута на основе домена (службы Master Data Services)](../master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
-   [Создание файлового атрибута (службы Master Data Services)](../master-data-services/create-a-file-attribute-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Сущности (службы Master Data Services)](../master-data-services/entities-master-data-services.md)   
 [Явные иерархии (службы Master Data Services)](../master-data-services/explicit-hierarchies-master-data-services.md)   
 [Изменение сущности (службы Master Data Services)](../master-data-services/edit-an-entity-master-data-services.md)   
 [Удаление сущности (службы Master Data Services)](../master-data-services/delete-an-entity-master-data-services.md)  
  
  
