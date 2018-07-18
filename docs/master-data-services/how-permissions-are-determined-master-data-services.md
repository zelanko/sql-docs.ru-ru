---
title: Способ определения разрешений (службы Master Data Services) | Документы Майкрософт
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
- permissions [Master Data Services], determining permissions
ms.assetid: 1dc0b43a-d023-4e7d-b027-8b1459fd058c
caps.latest.revision: 6
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: 1b21b2ec6561033451675a0683687af7a16757f3
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35407836"
---
# <a name="how-permissions-are-determined-master-data-services"></a>Способ определения разрешений (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Простейшим способом настройки безопасности служб [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]является назначение разрешений на объекты модели для группы, членом которой является пользователь.  
  
 Настройка безопасности становится более сложной в следующих случаях.  
  
-   Назначены разрешения как для объектов модели, так и для элементов иерархии.  
  
-   Пользователь принадлежит к группам, причем разрешения назначены как для пользователя, так и для групп.  
  
-   Пользователь принадлежит к группам, причем разрешения назначены для нескольких групп.  
  
## <a name="permissions-assigned-to-a-single-group-or-user"></a>Разрешения, назначенные одной группе или одному пользователю  
 Если разрешения назначаются одной группе или одному пользователю, они определяются на основании следующего рабочего процесса.  
  
 ![mds_conc_security_no_overlap](../master-data-services/media/mds-conc-security-no-overlap.gif "mds_conc_security_no_overlap")  
  
### <a name="step-1-effective-attribute-permissions-are-determined"></a>Шаг 1. Определяются действующие разрешения для атрибутов.  
 Следующий список показывает, как определяются действующие разрешения для атрибутов.  
  
-   Разрешения, назначенные для объектов модели, определяют, к каким атрибутам имеет доступ пользователь.  
  
-   Все объекты модели автоматически наследуют разрешение от ближайшего объекта на более высоком уровне в структуре модели.  
  
-   Всем объектам на том же уровне, на котором находится сущность, в разрешении неявно отказывается.  
  
-   Всем объектам на более высоком уровне предоставляется неявное разрешение на чтение. Дополнительные сведения о неявном разрешении на чтение см. в разделе [Навигационный доступ (службы Master Data Services)](../master-data-services/navigational-access-master-data-services.md).  
  
 В этом примере сущности назначается разрешение **Чтение**. Это же разрешение наследуется и атрибутом сущности, находящимся на более низком уровне структуры модели. Модель предоставляет неявное разрешение на чтение этой сущности и ее атрибуту. Другая сущность модели не имеет явно назначенного разрешения и не наследует никаких разрешений, поэтому доступ для нее неявно закрыт.  
  
 ![mds_conc_inheritance_model](../master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")  
  
### <a name="step-2-if-hierarchy-member-permissions-are-assigned-effective-member-permissions-are-determined"></a>Шаг 2. Если назначены разрешения для элементов иерархии, определяются действующие разрешения для элементов.  
 Следующий список показывает, как определяются действующие разрешения для элементов иерархии.  
  
-   Разрешения, назначенные для узлов иерархии, определяют, к каким элементам имеет доступ пользователь.  
  
-   Все узлы иерархии автоматически наследуют разрешение от ближайшего объекта на более высоком уровне в структуре иерархии.  
  
-   Всем узлам того же уровня в разрешении неявно отказывается.  
  
-   Любым узлам на более высоких уровнях, которые не имеют явно назначенных разрешений, в разрешении неявно отказывается.  
  
 В этом примере одному узлу иерархии назначается разрешение **Чтение** . Это же разрешение наследуется и узлом, находящимся на более низком уровне структуры иерархии. Корневому узлу разрешения не назначены, поэтому в разрешении ему неявно отказано. Другой узел в структуре иерархии не имеет явно назначенного разрешения и не наследует никаких разрешений, поэтому доступ для него неявно закрыт.  
  
 ![mds_conc_inheritance_hierarchy](../master-data-services/media/mds-conc-inheritance-hierarchy.gif "mds_conc_inheritance_hierarchy")  
  
### <a name="step-3-the-intersection-of-attribute-and-member-permissions-is-determined"></a>Шаг 3. Определяется пересечение разрешений для атрибутов и элементов.  
 Если действующие разрешения для атрибутов отличаются от действующих разрешений для элементов, разрешения должны определяться для каждого отдельного значения атрибута. Дополнительные сведения см. в разделе [Перекрытие разрешений моделей и элементов (службы основных данных)](../master-data-services/overlapping-model-and-member-permissions-master-data-services.md).  
  
## <a name="permissions-assigned-to-multiple-groups"></a>Разрешения, назначенные нескольким группам  
 Если пользователь принадлежит одной или более группам и разрешения назначены как пользователю, так и группам, рабочий процесс определения усложняется.  
  
 ![mds_conc_security_group_overlap](../master-data-services/media/mds-conc-security-group-overlap.gif "mds_conc_security_group_overlap")  
  
 В этом случае пересечения разрешений пользователя и группы должны определяться, прежде чем можно будет сравнивать разрешения для объектов модели и элементов иерархии. Дополнительные сведения см. в разделе [Перекрытие разрешений пользователей и групп (службы основных данных)](../master-data-services/overlapping-user-and-group-permissions-master-data-services.md).  
  
## <a name="see-also"></a>См. также:  
 [Перекрытие разрешений пользователей и групп (службы основных данных)](../master-data-services/overlapping-user-and-group-permissions-master-data-services.md)   
 [Перекрытие разрешений моделей и элементов (службы Master Data Services)](../master-data-services/overlapping-model-and-member-permissions-master-data-services.md)  
  
  
