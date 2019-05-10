---
title: Удаление группы атрибутов (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting attribute groups [Master Data Services]
- attribute groups [Master Data Services], deleting
ms.assetid: f915e89b-629d-4725-aea6-a7f051978244
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 4a913d9a49d2b1af43ea569bf40585c47432ef96
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65479562"
---
# <a name="delete-an-attribute-group-master-data-services"></a>Удаление группы атрибутов (службы Master Data Services)
  В службах [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно удалить группу атрибутов, если больше не нужна вкладка для отображения в функциональной области **Обозреватель** в среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
-   **Примечание.** Если группы атрибутов существуют, то атрибуты, не принадлежащие ни к одной группе, не отображаются в окне **Обозреватель**. Если групп атрибутов не существует, то отображаются все атрибуты.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](administrators-master-data-services.md).  
  
### <a name="to-delete-an-attribute-group"></a>Удаление группы атрибутов  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  На **представление модели** страницы, на панели меню наведите указатель мыши на **управление** и нажмите кнопку **группы атрибутов**.  
  
3.  Выберите модель из списка **Модель** .  
  
4.  Выберите сущность из списка **Сущность** .  
  
5.  Щелкните знак «плюс», чтобы развернуть **конечные группы**, **консолидированные группы**, или **группы коллекций**в зависимости от типа группы, необходимо будет удалить.  
  
6.  Щелкните группу атрибутов, которую необходимо удалить.  
  
7.  Нажмите кнопку **удалить выбранную группу**.  
  
8.  В диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
9. В дополнительном диалоговом окне подтверждения нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также  
 [Группы атрибутов (службы Master Data Services)](../../2014/master-data-services/attribute-groups-master-data-services.md)   
 [Создание группы атрибутов (службы Master Data Services)](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)  
  
  
