---
description: Разрешения функциональной области (службы Master Data Services)
title: Разрешения функциональной области
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- functional area permissions [Master Data Services], about functional area permissions
- functional area permissions [Master Data Services]
- permissions [Master Data Services], functional areas
ms.assetid: a80b87b3-b904-4cda-8582-0761c2617c57
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 0f3f863a6c08de5a4194c9fd6a08e4ee3e207e50
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88388330"
---
# <a name="functional-area-permissions-master-data-services"></a>Разрешения функциональной области (службы Master Data Services)

[!INCLUDE [SQL Server - Windows only ASDBMI  ](../includes/applies-to-version/sql-windows-only-asdbmi.md)]

  Разрешения можно назначать функциональным областям пользовательского интерфейса [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Ниже приведен список функциональных областей.  
  
-   **Обозреватель**  
  
-   **Управление версиями**  
  
-   **Управление интеграцией**  
  
-   **Системное администрирование**  
  
-   **Разрешения пользователей и групп**  
  
-   **Супер пользователь**  
  
 Если предоставляется разрешение на работу в функциональной области, эта область пользовательского интерфейса становится видимой для пользователя или группы.  
  
 Внутри функциональной области **Обозреватель** дополнительные разрешения на объекты модели и члены иерархии определяют, какие данные доступны пользователю. В остальных функциональных областях пользователь должен быть администратором модели, чтобы просматривать или использовать модель. Дополнительные сведения см. в разделе [administrators &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
> [!IMPORTANT]  
>  Пользователь с разрешениями суперпользователя получает права администратора для всех моделей, а также все остальные функциональные разрешения.  
  
 Чтобы иметь доступ к **, пользователь или группа должны иметь разрешение хотя бы для одной функциональной области и одной модели на вкладке** Модели [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Назначение разрешений функциональной области &#40;Master Data Services&#41;](../master-data-services/assign-functional-area-permissions-master-data-services.md)   
 [Разрешения объекта модели &#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [Разрешения элемента иерархии &#40;Master Data Services&#41;](../master-data-services/hierarchy-member-permissions-master-data-services.md)   
 [Способ определения разрешений (службы Master Data Services)](../master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  
