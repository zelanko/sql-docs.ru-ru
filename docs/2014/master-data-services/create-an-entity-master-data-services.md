---
title: Создание сущности (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], creating
- creating entities [Master Data Services]
ms.assetid: d9a6a51e-7b53-4785-a118-3baeb7ca2d48
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d85fc4c21f200bcdc5a489cfcee6b50bc9f4b98e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "65479915"
---
# <a name="create-an-entity-master-data-services"></a>Создание сущности (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]сущности создаются, чтобы содержать элементы и их атрибуты.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](administrators-master-data-services.md).  
  
-   Модель должна существовать. Дополнительные сведения см. в разделе [Создание модели (службы Master Data Services)](../../2014/master-data-services/create-a-model-master-data-services.md).  
  
### <a name="to-create-an-entity"></a>Создание сущности  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Представление модели** в строке меню наведите курсор на **Управление** и щелкните **Сущности**.  
  
3.  На странице **Обслуживание сущности** выберите модель из списка **Модель** .  
  
4.  Нажмите кнопку **добавить сущность**.  
  
5.  В поле **имя сущности** введите имя сущности.  
  
6.  В поле **имя для промежуточных таблиц** введите имя промежуточной таблицы.  
  
    > [!TIP]  
    >  Используйте имя модели как часть имени промежуточной таблицы, например *Modelname_Entityname*. Это облегчит поиск таблиц в базе данных. Дополнительные сведения о промежуточных таблицах см. в разделе [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).  
  
7.  Необязательный параметр. Установите флажок в поле **Автоматически создавать значения кода** . Дополнительные сведения см. в разделе [Автоматическое создание кодов (службы Master Data Services)](../../2014/master-data-services/automatic-code-creation-master-data-services.md).  
  
8.  В списке **включить явные иерархии и коллекции** выберите один из следующих вариантов.  
  
    -   **Нет**. Выберите этот параметр, если сущность не должна включать явные иерархии и коллекции. При необходимости это значение можно впоследствии изменить.  
  
    -   **Да**. Выберите этот параметр, если необходимо включить использование явных иерархий и коллекций. В поле **имя явной иерархии** введите имя. При необходимости выберите **обязательная иерархия (все конечные элементы включены** , чтобы сделать явную иерархию обязательной иерархией.  
  
9. Нажмите кнопку **Сохранить сущность**.  
  
## <a name="next-steps"></a>Next Steps  
  
-   [Создание текстового атрибута &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)  
  
-   [Создание атрибута на основе домена &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
-   [Создание атрибута файла &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
## <a name="see-also"></a>См. также:  
 [Сущности &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md)   
 [Явные иерархии &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)   
 [Измените имя сущности &#40;Master Data Services&#41;](edit-an-entity-master-data-services.md)   
 [Удаление сущности &#40;Master Data Services&#41;](../../2014/master-data-services/delete-an-entity-master-data-services.md)  
  
  
