---
title: Создание конечного элемента (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- leaf members [Master Data Services], creating
- creating leaf members [Master Data Services]
- members [Master Data Services], creating leaf members
ms.assetid: 0499d3b3-d508-4d43-a740-19cf53ade9f1
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: ffc3b726b0143b67a4991b8c22486259865ed804
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52822058"
---
# <a name="create-a-leaf-member-master-data-services"></a>Создание конечного элемента (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]создайте конечный элемент, если вам нужно добавить в систему основные данные. Если нужно добавить данные в массовом режиме, следует использовать промежуточные таблицы. Дополнительные сведения см. в разделе [Импорт данных из таблиц (службы Master Data Services)](../master-data-services/import-data-from-tables-master-data-services.md).  
  
 Также для импорта данных можно использовать [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] .  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   Необходимо иметь разрешение на доступ к функциональной области **Обозреватель** .  
  
-   Необходимо иметь как минимум разрешение **Создание** или **Обновление** для конечного объекта модели для сущности, в которую нужно добавить элемент. Разрешение "Создание" позволяет создать элемент и изменить только атрибут Code. Разрешение "Обновление" позволяет обновлять другие атрибуты.  
  
     Дополнительные сведения см. в разделе [Безопасность (службы Master Data Services)](../master-data-services/security-master-data-services.md).  
  
### <a name="to-create-a-leaf-member"></a>Создание конечного элемента  
  
1.  На домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] выберите модель в списке **Модель** .  
  
2.  Если вы пользователь, выберите открытую версию из списка **Версия** . Если вы являетесь администратором, выберите версию в открытом или блокированном состоянии из списка **Версия** .  
  
3.  Нажмите кнопку **Браузер**.  
  
4.  В строке меню наведите указатель на пункт **Сущности** и щелкните имя сущности, к которой нужно добавить элемент.  
  
5.  Нажмите кнопку **Добавить элемент**.  
  
6.  Заполните поля в области **Сведения** .  
  
     Если фильтр применен к атрибуту, который основан на домене, список значений атрибута будет ограничен родительским атрибутом фильтра.  
  
     Дополнительные сведения о родительских атрибутах фильтров и атрибутах на основе домена см. в разделе [Создание атрибута на основе домена (службы Master Data Services)](../master-data-services/create-a-domain-based-attribute-master-data-services.md).  
  
7.  Необязательный параметр. В поле **Заметки** введите комментарий о том, для чего добавлен элемент. Заметку могут просматривать все пользователи, которые имеют доступ к элементу.  
  
8.  Нажмите кнопку **ОК**.  
  
## <a name="see-also"></a>См. также:  
 [Создание объединенного элемента (службы Master Data Services)](../master-data-services/create-a-consolidated-member-master-data-services.md)   
 [Элементы (службы Master Data Services)](../master-data-services/members-master-data-services.md)  
  
  
