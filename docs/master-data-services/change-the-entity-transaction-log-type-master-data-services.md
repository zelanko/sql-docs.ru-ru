---
title: Изменение типа журнала транзакций сущности
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 75250b32-3384-43c2-9b5c-1607cc3aa7b3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fde8e314462846088c7c673524d6e6d8d29ee631
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73729663"
---
# <a name="change-the-entity-transaction-log-type-master-data-services"></a>Изменение типа журнала транзакций сущности (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Можно изменить тип журнала транзакций сущности, чтобы вести его на уровне атрибутов, элементов или не вести вообще.  
  
|Тип журнала транзакций|Описание|  
|--------------------------|-----------------|  
|Attribute|Журналы изменений сущности сохраняются на уровне атрибутов.<br /><br /> Журнал транзакций сохраняется как и для [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].|  
|Член|Журналы изменений сущности сохраняются на уровне строк.<br /><br /> Любое изменение атрибута инициирует новую версию строк.<br /><br /> При использовании журнала транзакций уровня строк сущность сохраняется как медленно меняющееся измерение типа 4. Поддерживаются представления подписки типов 2 и 4 (журнал). Дополнительные сведения см. в разделе [Форматы представления подписки (Master Data Services)](../master-data-services/subscription-view-formats-master-data-services.md).<br /><br /> Обеспечивается лучшая производительность.|  
|None|Журналы изменений не сохраняются.<br /><br /> Обеспечивается наилучшая производительность.|  
  
## <a name="prerequisites"></a>Предварительные требования  
 Чтобы выполнить эту процедуру:  
  
-   необходимо разрешение на доступ к функциональной области "Администрирование системы"; см. раздел [Разрешения функциональной области (службы Master Data Services)](../master-data-services/functional-area-permissions-master-data-services.md);  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md).  
  
-   Сущность должна существовать. Дополнительные сведения см. в разделе [Создание сущности (службы Master Data Services)](../master-data-services/create-an-entity-master-data-services.md).  
  
 **Изменение типа журнала транзакций**  
  
1.  В диспетчере основных данных щелкните **Системное администрирование**.  
  
2.  На странице **Manage Model** (Управление моделью) в сетке выберите строку модели для сущности, которую необходимо изменить, а затем щелкните **Сущности**.  
  
3.  На странице **Manage Entity** (Управление сущностью) в сетке выберите строку сущности, которую необходимо обновить, а затем щелкните **Изменить**.  
  
4.  Из раскрывающегося списка выберите тип журнала транзакций.  
  
5.  Нажмите кнопку **Сохранить**.  
  
  
