---
title: Удаление разрешений для объекта модели (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting model object permissions [Master Data Services]
- permissions [Master Data Services], deleting model object permissions
- models [Master Data Services], deleting object permissions
ms.assetid: 859c5952-f600-4940-8064-1afd13f7f6dc
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 1a0cb087f5a0cd429d9bc6f30ea08aaef3d07b3b
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65483107"
---
# <a name="delete-model-object-permissions-master-data-services"></a>Удаление разрешений для объекта модели (службы Master Data Services)
  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]удалите разрешения на объект модели для отмены любых существующих назначений.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Разрешения пользователей и групп** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](administrators-master-data-services.md).  
  
### <a name="to-delete-model-object-permissions"></a>Удаление разрешений объекта модели  
  
1.  В среде [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните **Разрешения пользователей и групп**.  
  
2.  На странице **Пользователи** или **Группы** выберите строку пользователя или группы, которые необходимо изменить.  
  
3.  Нажмите **Изменить выделенного пользователя**.  
  
4.  Перейдите на вкладку **Модели** .  
  
5.  По желанию выберите модель из списка **Модель** .  
  
6.  В **Сводка по разрешениям модели** области, выберите строку для разрешения, которое требуется удалить.  
  
7.  Нажмите кнопку **удалить выбранное разрешение**.  
  
    > [!NOTE]  
    >  Нельзя удалить разрешение у пользователя, если разрешение унаследовано от группы. В этом случае нужно отозвать разрешение у группы.  
  
## <a name="see-also"></a>См. также  
 [Разрешения объекта модели (службы Master Data Services)](../../2014/master-data-services/model-object-permissions-master-data-services.md)   
 [Назначение разрешения для объекта модели (службы Master Data Services)](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md)  
  
  
