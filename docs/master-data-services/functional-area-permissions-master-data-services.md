---
title: Разрешения функциональной области (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.suite: sql
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- functional area permissions [Master Data Services], about functional area permissions
- functional area permissions [Master Data Services]
- permissions [Master Data Services], functional areas
ms.assetid: a80b87b3-b904-4cda-8582-0761c2617c57
caps.latest.revision: 10
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: e2f44e7ae9d18721ebda0571bc5d883f789ec18b
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35411726"
---
# <a name="functional-area-permissions-master-data-services"></a>Разрешения функциональной области (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Разрешения можно назначать функциональным областям пользовательского интерфейса [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Ниже приведен список функциональных областей.  
  
-   **Обозреватель**  
  
-   **Управление версиями**  
  
-   **Управление интеграцией**  
  
-   **Администрирование системы**  
  
-   **Разрешения пользователей и групп**  
  
-   **Суперпользователь**  
  
 Если предоставляется разрешение на работу в функциональной области, эта область пользовательского интерфейса становится видимой для пользователя или группы.  
  
 Внутри функциональной области **Обозреватель** дополнительные разрешения на объекты модели и члены иерархии определяют, какие данные доступны пользователю. В остальных функциональных областях пользователь должен быть администратором модели, чтобы просматривать или использовать модель. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
> [!IMPORTANT]  
>  Пользователь с разрешениями суперпользователя получает права администратора для всех моделей, а также все остальные функциональные разрешения.  
  
 Чтобы иметь доступ к **, пользователь или группа должны иметь разрешение хотя бы для одной функциональной области и одной модели на вкладке** Модели [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Назначение разрешений для функциональной области (службы Master Data Services)](../master-data-services/assign-functional-area-permissions-master-data-services.md)   
 [Разрешения объекта модели (службы Master Data Services)](../master-data-services/model-object-permissions-master-data-services.md)   
 [Разрешения на элементы иерархии (службы Master Data Services)](../master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Способ определения разрешений (службы Master Data Services)](../master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
