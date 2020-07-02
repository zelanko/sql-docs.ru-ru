---
title: Изменение имени атрибута и типа данных
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], changing name
ms.assetid: d348f238-f59d-41c7-ad20-3ccd55bfd9e5
author: lrtoyou1223
ms.author: lle
manager: erikre
ms.openlocfilehash: cb7d82f63f41baa88523f97e45a65635e1d49486
ms.sourcegitcommit: 6be9a0ff0717f412ece7f8ede07ef01f66ea2061
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85813468"
---
# <a name="change-an-attribute-name-and-data-type-master-data-services"></a>Изменение имени атрибута и типа данных (службы Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно изменять имя атрибутов.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** .  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### <a name="to-change-an-attribute-name-and-type"></a>Изменение имени атрибута и типа данных  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На странице **Управление моделью** выберите модель в сетке и щелкните **сущности**.  
  
3.  На странице **Управление сущностью** выберите строку сущности, для которой необходимо создать атрибут.  
  
4.  Нажмите **Атрибуты**.  
  
5.  На странице **Управление атрибутами** выполните одно из следующих действий:  
  
    -   Если атрибут предназначен для конечных элементов, в списке **Типы членов** выберите **Конечный элемент** .  
  
    -   Если атрибут предназначен для консолидированных элементов, в списке **Типы членов** выберите **Консолидированный элемент** .  
  
    -   Если атрибут предназначен для коллекций, в списке **Типы членов** выберите **Коллекция** .  
  
6.  Выберите строку для атрибута, который необходимо изменить, а затем нажмите **Изменить**.  
  
7.  Введите новое имя атрибута в поле **Имя** . Список слов, которые не должны использоваться в качестве имен атрибутов, см. в разделе [зарезервированные слова &#40;Master Data Services&#41;](../master-data-services/reserved-words-master-data-services.md).  
  
8.  Выберите другой тип в списке **Тип атрибута** .  
  
9. Выберите команду **Сохранить**.  
  
## <a name="see-also"></a>См. также  
 [Создание текстового атрибута &#40;Master Data Services&#41;](../master-data-services/create-a-text-attribute-master-data-services.md)   
 [Удаление атрибута &#40;Master Data Services&#41;](../master-data-services/delete-an-attribute-master-data-services.md)   
 [Атрибуты (службы Master Data Services)](../master-data-services/attributes-master-data-services.md)  
  
  
